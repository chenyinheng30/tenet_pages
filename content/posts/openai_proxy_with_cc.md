---
title: 使用 cloudfare 反向代理 openai 的 API，并使用客户端证书防止滥用
subtitle:
date: 2023-11-16T12:21:21+08:00
draft: false
author:
  name:
  link:
  email:
  avatar:
description:
keywords:
license:
comment: false
weight: 0
tags:
  - cloudflare
  - openai
  - 反向代理
  - api
  - ai
  - 人工智能
categories:
  - cloudflare
hiddenFromHomePage: false
hiddenFromSearch: false
summary:
resources:
  - name: featured-image
    src: featured-image.jpg
  - name: featured-image-preview
    src: featured-image-preview.jpg
toc: true
math: false
lightgallery: true
password:
message:
repost:
  enable: true
  url:

# See details front matter: https://fixit.lruihao.cn/documentation/content-management/introduction/#front-matter
---

## 简单的步骤说明

1. 申请域名
2. 注册并登陆 cloudfare 的控制台(dash)
3. 更改 DNS 的名称服务器
4. 创建 cloudfare worker
5. 配置客户端证书
6. 使用 wft 限制访问

以下假设已有 cloudfare 账号，上面的步骤 2 就省略了。

## 注册域名并更改名称服务器

在相关的网站注册心意的域名就行，国内流行的就是阿里云、腾讯云等。

其实也可以直接在 cloudflare.com 注册域名，不过要绑定支付方式，但是就省去了更改 DNS 的名称服务器等步骤。

如果不是在 cloudflare.com 注册域名，就需要按以下的更改名称服务器：

首先在 dash 选择「网站」，然后点击「添加网站」，输入申请的域名点击「继续」

![添加网站](/images/openai_proxy_with_cc_Zi1Cv1.png)

然后在注册域名的网站更改名称服务器为 `dilbert.ns.cloudflare.com` 和 `luciane.ns.cloudflare.com` ，在阿里云的操作如下：

首先登陆阿里云控制台，在「我的资源」下点击「域名」

![进入域名界面](/images/openai_proxy_with_cc_OfZxTf.png)

选择相应的域名，之后点击「DNS修改」填入 cloudflare.com 的两个名称服务器就行

![修改名称服务器](/images/openai_proxy_with_cc_vvZHVY.png)

## 创建 cloudfare worker

在 cloudfare 控制台选择「Workers 和 Pages」

![在控制台选择「Workers 和 Pages」](/images/openai_proxy_with_cc_HgUUxa.png)

点击「创建应用程序」、「创建Worker」输入合适的名称，点击「部署」

![部署Worker](/images/openai_proxy_with_cc_eZMXW3.png)

然后点击「编辑代码」，将代码更改为：

```json
const TELEGRAPH_URL = 'https://api.openai.com';

addEventListener('fetch', event => {
  event.respondWith(handleRequest(event.request))
})

async function handleRequest(request) {
  const url = new URL(request.url);
  url.host = TELEGRAPH_URL.replace(/^https?:\/\//, '');

  const modifiedRequest = new Request(url.toString(), {
    headers: request.headers,
    method: request.method,
    body: request.body,
    redirect: 'follow'
  });

  const response = await fetch(modifiedRequest);
  const modifiedResponse = new Response(response.body, response);

  // 添加允许跨域访问的响应头
  modifiedResponse.headers.set('Access-Control-Allow-Origin', '*');

  return modifiedResponse;
}
```

之后在「触发器」中「添加自定义域」为相应子域名就行。之后就可以访问 openai 的 API 而不会有 403 的问题了。

## 配置客户端证书并使用 wft 限制访问

首先申请证书，在「站点」、「SSL/TLS」下选择「客户端证书」，然后「创建证书」，最后添加子域名启动 mTLS，最终效果如图

![最终效果](/images/openai_proxy_with_cc_cq3XMV.png)

在添加证书过程中会保留一个密匙与证书的文件，一般分别命名为 `expamle.com.key` 和 `expamle.com.pem`，应用这两个文件就可以访问自己定义的子域名了。