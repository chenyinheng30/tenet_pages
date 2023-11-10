---
title: 第一类完全椭圆积分
subtitle:
date: 2023-11-10T09:41:34+08:00
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
  - 椭圆函数
  - 积分
  - 有理函数
categories:
  - 数学
hiddenFromHomePage: false
hiddenFromSearch: false
summary:
resources:
  - name: featured-image
    src: featured-image.jpg
  - name: featured-image-preview
    src: featured-image-preview.jpg
toc: true
math: true
lightgallery: false
password:
message:
repost:
  enable: true
  url:

# See details front matter: https://fixit.lruihao.cn/documentation/content-management/introduction/#front-matter
---

第一类完全椭圆积分有着这样的形式

$$
\int_0^{\pi/2} {\frac{d\phi}{\sqrt{1-k^2sin^2\phi}}}
$$

可以写成 $F(k,\pi/2)$ 或 $F(k)$.

## 算术几何中值

有数列 $a_n,\ b_n$ 且有 $a_1=a,b_1=b,a_1>b_1>0$ 有如下递推式

$$
a_{n+1}=\frac{a_n+b_n}{2},\ b_{n+1}=\sqrt{a_nb_n}
$$

用归纳法可证得 $a_n$ 递增， $b_n$ 递减，并且 $a_n>0,\ b_n>0$. 可以得到 $\lim_{n\rightarrow\infty} a_n$ 存在.又

{{< raw >}}
$$
\begin{aligned}
a_{n+1}-b_{n+1} &\le  a_{n+1}-b_n=\frac{a_n+b_n}{2}-b_n=\frac{1}{2}(a_n-b_n) \\
a_{n+1}-b_{n+1} &\le \frac{1}{2^n}(a_1-b_1)
\end{aligned}
$$
{{< /raw >}}

所以 $\lim_{n\rightarrow\infty} a_n-b_n$ 极限存在，得到 $\lim_{n\rightarrow\infty} a_n = \lim_{n\rightarrow\infty} b_n$ 称此极限为 $a_1,b_1$ 算术几何中值用 $\mu(a,b)$ 表示.

## 高斯公式

考虑积分

$$
G=\int_0^{\pi/2} {\frac{d\phi}{\sqrt{a^2cos^2\phi+b^2sin^2\phi}}},\ a>b>0
$$

由公式，有替换

$$
sin\phi=\frac{2asin\theta}{(a+b)+(a-b)sin^2\theta}
$$

另上式右边的分母=Y有以下关系可以简化计算

{{< raw >}}
$$
\begin{aligned}
    &[(a+b)+(a-b)sin\theta^2]^2-4a^2sin^2\theta= [(a+b)-(a-b)sin\theta^2]^2-4b^2sin^2\theta \\
    &[(a+b)+(a-b)sin\theta^2]^2+[(a+b)-(a-b)sin\theta^2]^2=2[(a+b)^2+(a-b)^2sin^4\theta]
\end{aligned}
$$
{{< /raw >}}

即是

{{< raw >}}
$$
\begin{aligned}
cos\phi d\phi&=2a\frac{(a+b)-(a-b)sin^2\theta}{Y^2}cos\theta d\theta \\
cos\phi&=\frac{\sqrt{(a+b)^2-(a-b)^2sin^2\theta}}{Y}cos\theta \\
\sqrt{a^2cos^2\phi+b^2sin^2\phi}&=a\frac{(a+b)-(a-b)sin^2\theta}{Y}\frac{d\theta}{\sqrt{(a+b)^2-(a-b)^2sin^2\theta}}
\end{aligned}
$$
{{< /raw >}}

得到

$$
\frac{d\phi}{\sqrt{a^2cos^2\phi+b^2sin^2\phi}}=\frac{d\theta}{\sqrt{(\frac{a+b}{2})^2cos^2\theta+absin^2\theta}}
$$

令 $a_1=a,\ b_1=b$，则

$$
G=\int_0^{\pi/2} {\frac{d\phi}{\sqrt{a_1^2cos^2\phi+b_1^2sin^2\phi}}}
$$

反复利用变换得到

$$
G=\int_0^{\pi/2} {\frac{d\phi}{\sqrt{a_n^2cos^2\phi+b_n^2sin^2\phi}}}
$$

其中的 $a_n,\ b_n$ 有递推关系

$$
a_{n}=\frac{a_{n-1}+b_{n-1}}{2},\ b_{n}=\sqrt{a_{n-1}b_{n-1}}
$$

又有不等式

$$
\pi/(2a_n) < G < \pi/(2b_n)
$$

取极限得到

$$
G=\frac{\pi}{2\mu(a,b)}
$$
