---
title: 椭圆积分
subtitle:
date: 2023-11-11T11:21:21+08:00
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
  - 椭圆积分
  - 椭圆函数
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

## 阿贝尔积分

考虑形如

{{< raw >}}
$$
\int{R(x,y)dy} \tag{1}
$$
{{< /raw >}}

且有 $x,y$ 满足他们的多项式方程 $P(x,y)=0$ ，这一形状的积分被称为**阿贝尔积分**.例如 $\int{R(x,\sqrt{\frac{ax+b}{cx+d}})dx}$ 与 $\int{R(x,\sqrt{ax^2+bx+c})dx}$ 都是**阿贝尔积分**.

如果曲线 $P(x,y)=0$ 可以被表示为参数方程

{{< raw >}}
$$
\begin{cases}
x=r_1(t) \\
y=r_2(t)
\end{cases}
$$
{{< /raw >}}

其中的 $r_1(t)$ , $r_2(t)$ 为有理函数.则曲线 $P(x,y)=0$ 被称为有理曲线.那么有替换 $x=r_1(t)$ 得到积分

{{< raw >}}
$$
\int{R(r_1(t),r_2(t))\dot{r}_1(t)dt}
$$
{{< /raw >}}

为有理函数积分，即可用有理函数积分的方法求出.

但是曲线 $P(x,y)=0$ 并不总是有理曲线，所以(1)并不总是可以换元成有理函数的形式，**椭圆积分** 就是这样的类型.

## 椭圆积分的形式

椭圆积分也是阿贝尔积分的一类，通常有一下的形式

{{< raw >}}
$$
\int{R(x,\sqrt{ax^3+bx^2+cx+d})dx} \tag{2}
$$
{{< /raw >}}

{{< raw >}}
$$
\int{R(x,\sqrt{ax^4+bx^3+cx^2+dx+e})dx} \tag{3}
$$
{{< /raw >}}

因为三次多项式 $ax^3+bx^2+cx+d$ 一定有实根，假设 $\lambda$ 是三次多项式的实根有

{{< raw >}}
$$
ax^3+bx^2+cx+d = a(x-\lambda)(x^2+px+q)
$$
{{< /raw >}}

又有替换 $x-\lambda=t^2$ 有

{{< raw >}}
$$
\int{R(x,\sqrt{ax^3+bx^2+cx+d})dx}=\int{R(t^2+\lambda,\sqrt{at^4+...})dx}
$$
{{< /raw >}}

就将积分(2)转化为了积分(3)的形式，所以对于椭圆积分只要考虑形式(3)即可.

## $y=\sqrt{ax^4+...}$ 的椭圆积分

一般的四次多项式可以化为两个二次多项式的形式

{{< raw >}}
$$
ax^4+bx^3+cx^2+dx+e=a(x^2+px+q)(x^2+p^{'}x+q^{'})
$$
{{< /raw >}}

现在想办法将两个二次多项式中的一次项去掉，当 $p=p^{'}$ 时有替换 $x=t-\frac{p}{2}$ 得

{{< raw >}}
$$
a(x^2+px+q)(x^2+p^{'}x+q^{'})=a(t^2+\frac{p^2}{2}+q)(t^2+\frac{p^2}{2}+q^{'})
$$
{{< /raw >}}

当 $p \neq p^{'}$ 选择合适的替换 $x=\frac{\mu t+
v }{t+1}$ 有

{{< raw >}}
$$
x^2+px+q=\frac {(\mu ^2+p\mu +q)t^2+(2\mu 
v +p(\mu +
v )+2q)t+(
v ^2+p
v +q)}{(t+1)^2}
$$
{{< /raw >}}

令

{{< raw >}}
$$
\begin{cases}
2\mu 
v +p(\mu +
v )+2q=0 \\
2\mu 
v +p^{'}(\mu +
v )+2q^{'}=0
\end{cases}
$$
{{< /raw >}}

得

{{< raw >}}
$$
\mu + v =2\frac{q-q^{'}}{p-p^{'}},\quad
\mu v =\frac{p^{'}q-pq^{'}}{p-p^{'}}
$$
{{< /raw >}}

所以 $\mu ,
v$ 是方程 $(p-p^{'})z^2+2(q-q^{'})t+(p^{'}q-pq^{'})=0$ 的两个相异的实数根.

根据上面两个换元的方法可以得到

{{< raw >}}
$$
\int{R(x,\sqrt{ax^2+...})dx}=\int{R(\frac{\mu t+
v }{t+1},\sqrt{\frac{(M+Nt^2)(M^{'}+N^{'}t^2)}{(t+1)^2}})\frac{\mu -
v }{(t+1)^2}dt}
$$
{{< /raw >}}

当 $M,M^{'},N,N^{'}$ 都不为 $0$ （以及 $p=p^{'}$ ）时可以改写成以下的情况

{{< raw >}}
$$
\int{R(t,\sqrt{A(1+mt^2)(1+m^{'}t^2)})dt}
$$
{{< /raw >}}

其中，令 $y=\sqrt{A(1+mt^2)(1+m^{'}t^2)}$ 得

{{< raw >}}
$$
R(t,y)=\frac {P_1(t) + P_2(t)y} {P_3(t) + P_4(t)y}
$$
{{< /raw >}}

分子分母同乘 $P_3(t) - P_4(t)y$ 得

{{< raw >}}
$$
R(t,y)=R_1(t)+R_2(t)y
$$
{{< /raw >}}

右边第一项为有理函数容易求解，右边可以写成 $R_2(t)y=R_2(t)\frac{(y^2)}{y}=R^*(t)\frac{1}{y}$ ，得到右边的积分为

{{< raw >}}
$$
\int {\frac{R^*(t)}{\sqrt{A(1+mt^2)(1+m^{'}t^2)}}dt}
$$
{{< /raw >}}

$R^*(t)$ 可以分成两个部分

{{< raw >}}
$$
R^*(t)=\frac{R^*(t)+R^*(-t)}{2} + \frac{R^*(t)-R^*(-t)}{2}
$$
{{< /raw >}}

右边的第一项为偶函数可以写成 $t^2$ 的函数 ${R_1}^*(t^2)$ ，第二项为奇函数可以写成 ${R_2}^*(t^2)t$ ，有积分

{{< raw >}}
$$
\int {\frac{R^*(t)}{\sqrt{A(1+mt^2)(1+m^{'}t^2)}}dt}=\int {\frac{{R_1}^*(t^2)}{\sqrt{A(1+mt^2)(1+m^{'}t^2)}}dt}+\int {\frac{{R_2}^*(t^2)t}{\sqrt{A(1+mt^2)(1+m^{'}t^2)}}dt}
$$
{{< /raw >}}

右边第二项可以将 $t^2=u$ 带入得到

{{< raw >}}
$$
\int {\frac{{R_2}^*(t^2)t}{\sqrt{A(1+mt^2)(1+m^{'}t^2)}}dt}=1/2\int {\frac{{R_2}^*(u)}{\sqrt{A(1+mu)(1+m^{'}u)}}du}
$$
{{< /raw >}}

只需要再考虑右边第一项

{{< raw >}}
$$
\int {\frac{{R_1}^*(t^2)}{\sqrt{A(1+mt^2)(1+m^{'}t^2)}}dt} \tag{4}
$$
{{< /raw >}}

(4)的形式可以化为**标准形式**

{{< raw >}}
$$
\int {\frac{R(z^2)}{\sqrt{(1-z^2)(1-k^2z^2)}}dz} \tag{5},\ 0 < k < 1
$$
{{< /raw >}}

## 第一、第二、第三类椭圆积分

(5) 可以是以下的积分的线性组合

{{< raw >}}
$$
I_n=\int {\frac{z^{2n}}{\sqrt{(1-z^2)(1-k^2z^2)}}dz},\  n=0,1,2,... \\
H_m=\int {\frac{dz}{(z^2-a)^m\sqrt{(1-z^2)(1-k^2z^2)}}},\ a为复数,m=1,2,3,...
$$
{{< /raw >}}

令 $Y=(1-z^2)(1-k^2z^2)$ ,得

{{< raw >}}
$$
Y = \sum_{i=0}^2 {a_iz^{2i}} \\
\dot Y = \sum_{i=1}^2 {2ia_iz^{2i-1}} \\
(\sqrt{Y})^{'}=\frac{\dot Y}{2\sqrt{Y}}
$$
{{< /raw >}}

考虑

{{< raw >}}
$$
\begin{aligned}
(z^j\sqrt {Y})^{'}&=jz^{j-1}\sqrt{Y}+\frac{z^j\dot Y}{2\sqrt{Y}} \\
&=\frac{2jz^{j-1}Y+z^j\dot Y}{2\sqrt{Y}} \\
&=ja_0\frac{z^{j-1}}{\sqrt{Y}}+(j+1)a_1\frac{z^{j+1}}{\sqrt{Y}}+(j+2)a_2\frac{z^{j+3}}{\sqrt{Y}}
\end{aligned}
$$
{{< /raw >}}

令 $j+3=2n$ ，又 $Y=1-(1+k^2)z^2+k^2z^4$ 得

{{< raw >}}
$$
\begin{aligned}
d(z^{2n-3}\sqrt {Y})&=(2n-3)d(\frac{z^{2n-4}}{\sqrt{Y}})-(2n-2)(k^2+1)d(\frac{z^{2n-2}}{\sqrt{Y}})+(2n-1)k^2d(\frac{z^{2n}}{\sqrt{Y}}) \\
&=(2n-3)dI_{n-2}-(2n-2)(k^2+1)dI_{n-1}+(2n-1)k^2dI_n
\end{aligned}
$$
{{< /raw >}}

所以

{{< raw >}}
$$
z^{2n-3}\sqrt {Y}=(2n-3)I_{n-2}-(2n-2)(k^2+1)I_{n-1}+(2n-1)k^2I_n
$$
{{< /raw >}}

带入 $n=2,3,...$

{{< raw >}}
$$
\begin{aligned}
I_2&=z\sqrt{Y}/(3k^2)-I_0/(3k^2)+2(1+k^2)I_1/(3k^2) \\
I_3&=z^3\sqrt{Y}/(5k^2)-3I_1/(5k^2)+4(k^2+1)I_2/(5k^2) \\
&\qquad\qquad\qquad\qquad\quad\vdots
\end{aligned}
$$
{{< /raw >}}

将 $I_2$ 的右边带入 $I_3$ ，设 $Q_n(x)$ 为x的n阶多项式 $I_3$ 可以写成以下形式

{{< raw >}}
$$
I_3=\alpha_3I_0+\beta_3I_1+zQ_1(z^2)\sqrt{Y}
$$
{{< /raw >}}

考虑一般的情况有

{{< raw >}}
$$
I_n=\alpha_nI_0+\beta_nI_1+zQ_{n-2}(z^2)\sqrt{Y} \tag{6}
$$
{{< /raw >}}

对等式(6)两边分别求导，就可以用待定系数发算出 $\alpha_n,\beta_n,Q_{n-2}(z^2)$ ，所以求积分 $I_n$ 的关键在计算 $I_0, I_1$ .其中 $I_0=\int\frac{dz}{\sqrt{(1-z^2)(1-k^2z^2)}}$ ，进行替换 $z=sin(\phi)$ ，就得到了**勒让德第一类椭圆积分**

{{< raw >}}
$$
\int {\frac{d\phi}{\sqrt{1-k^2sin^2(\phi)}}},\ 0 < k < 1
$$
{{< /raw >}}

对 $I_1=\int\frac{z^2dz}{\sqrt{(1-z^2)(1-k^2z^2)}}$ 也做同样的变换，得到

{{< raw >}}
$$
I_1=1/k^2\int {\frac{d\phi}{\sqrt{1-k^2sin^2(\phi)}}} - 1/k^2\int {\sqrt{1-k^2sin^2(\phi)}d\phi}
$$
{{< /raw >}}

右边的第二项就是**勒让德第二类积分**

{{< raw >}}
$$
\int {\sqrt{1-k^2sin^2(\phi)}d\phi},\ 0 < k < 1
$$
{{< /raw >}}

类似对 $H_n$ 有类似递推式

{{< raw >}}
$$
a_mH_{m}+b_mH_{m-1}+c_mH_{m-2}+d_mH_{m-3}=\frac{z}{(z^2-a)^m}\sqrt{Y}
$$
{{< /raw >}}

考虑 $H_1,H_0,H_{-1}$

{{< raw >}}
$$
\begin{aligned}
H_1 &= \int {\frac{dz}{(z^2-a)\sqrt{(1-z^2) (1-k^2z^2)}}} \\
H_0 &= \int {\frac{dz}{\sqrt{(1-z^2) (1-k^2z^2)}}} \\
&= I_0 \\
H_{-1} &= \int {\frac{(z^2-a)dz}{\sqrt{(1-z^2) (1-k^2z^2)}}} \\
&=I_1-aI_0
\end{aligned}
$$
{{< /raw >}}

所以 $H_m$ 可以写成

{{< raw >}}
$$
H_m=\alpha_mI_0+\beta_mI_1+\gamma_mH_1+zQ_{m-1}(1/(z^2-a))\sqrt{Y}
$$
{{< /raw >}}

当 $a \neq 0$ 令 $h=-1/a$ ，再有替换 $z=sin(\phi)$ 可以得到得**勒让德第三类积分**

{{< raw >}}
$$
\int {\frac{d\phi}{(1+hsin^2(\phi))\sqrt{(1-k^2sin^2(\phi))}}},\ 0 < k < 1
$$
{{< /raw >}}
