---
layout: post
title: 'LaTex的使用'
date: 2018-10-23
categories: markdown
cover: https://image.mmschool.club/github/sun.jpg
tags: markdown
---
参考：https://blog.csdn.net/kevinelstri/article/details/62419242

## Markdown中使用LaTeX
在markdown中，LaTex有两种，一种是独行显示，一种是在文本内显示

```
#行内
$\sum_{i=1}^{N}n$
#独行
$$\sum_{i=1}^{N}n$$
```
行内显示$\sum_{i=1}^{N}n$，或者独行显示$$\sum_{i=1}^{N}n$$


|小写命令	|小写显示|小写命令	|小写显示|小写命令	|小写显示|
|--|--|--|--|--|--|
|\alpha	|α|\pi	|π|\eta	|η|
|\beta	|β|\rho	|ρ|\iota	|ι|
|\gamma	|γ|\sigma	|σ|\kappa	|κ|
|\theta	|θ|\tau	|τ|\lambda|λ|
|\delta	|δ|\phi	|ϕ|\mu	|μ|
|\epsilon|ϵ|\omega	|ω|\nu	|ν|
|\zeta	|ζ|

$$
\begin{matrix}
    1&2&3 \\
    4&5&6 \\
    7&8&9
\end{matrix}
$$

$$
\left \{
	\begin{matrix}
		1&2&3\\
		4&5&6\\
		7&8&9
	\end{matrix}
\right \} \tag{3}


$$

$$
\begin{bmatrix}
    		1&2&3\\
		4&5&6\\
		7&8&9
\end{bmatrix}
$$

$$
\begin{Bmatrix}
    	1&2&3\\
		4&5&6\\
		7&8&9
\end{Bmatrix}
$$


$$
\beta=\frac{\alpha}{\sum_{i=2}^{n}} \tag{55}
$$


