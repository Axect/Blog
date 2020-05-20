---
title: "🐪 Gaussian Conquest"
date: 2020-05-20T23:01:29+09:00
draft: false
toc: true
images:
tags:
  - mathematics
  - statistics
---

물리학이나 통계학 등을 하다보면 항상 마주치는 원수 같은 존재가 있습니다. 별로 어렵지는 않은데 마주칠 때마다 헷갈리는 그 존재는 바로 **가우스 적분**(Gaussian Integral)입니다.

$$\int_{-\infty}^\infty e^{-\alpha x^2} dx$$

이공계 대학생이라면 1학년 미적분학 시간에 극좌표계(Polar coordinate)를 이용한 이중적분을 다룰 때 나오는 가장 기본문제로 가우스 적분을 기억할겁니다. 그러나 항상 거의 모두가 그렇듯이 시간이 지나면 지날 수록 기억은 풍화되고 거의 망각의 단계에 이르렀을 때에 갑자기 튀어나오는 낯선 형태의 가우스 적분들은 대처하기가 난감합니다.

따라서 여기서는 가우스 적분과 가우시안 분포에 대한 아주 기본적인 성질들을 다시 상기시키고 이를 발판삼아 다변수 가우시안(Multivariate Gaussian)과 여러 활용들을 살펴보도록 하겠습니다.

-----

## 🔢 기본적인 가우스 적분 (Basic Gaussian Integral)

**이해하기 위해 필요한 개념**
* 고교 수준의 적분 (치환 적분, 지수함수의 적분)
* 극좌표계
* 이중적분

가우스 적분은 전형적인 *처음 하기는 힘들지만 한 번 보면 누구나 할 수 있는* 형태의 스킬입니다. 이것을 보고 극좌표계에서의 이중적분을 떠올리기는 힘들지만 그것을 사용한다는 것을 깨닫는 순간 문제는 아주 기초적인 미적분 문제로 격하됩니다. 그럼 먼저 가장 기본적인 가우스 적분을 봅시다.


### 1) 1D Gaussian Integral

$$
\int_{-\infty}^\infty e^{-\alpha x^2} dx = \sqrt{\frac{\pi}{\alpha}}
$$

> 이것을 바로 증명하기에는 어려움이 있으므로 제곱 꼴을 고려해야 합니다.
> $$\left(\int_{-\infty}^\infty e^{-\alpha x^2}\right)^2 = \int_{-\infty}^\infty \int_{-\infty}^\infty e^{-\alpha(x^2 + y^2)} dx dy$$
> 이것을 $x^2 + y^2 = r^2,~dxdy = rdrd\theta$임을 이용하여 극좌표계 적분으로 변환합니다. 그렇다면 아주 간단한 치환 적분으로 적분을 계산할 수 있습니다.
> $$\int_{0}^\infty \int_{0}^{2\pi} re^{-\alpha r^2} dr d\theta = 2\pi\int_0^\infty e^{-t} \frac{dt}{2\alpha} = \frac{\pi}{\alpha}$$
> 가우스 적분의 제곱이 위와 같은 결과가 되었고, 가우시안 함수($e^{-\alpha x^2}$)는 항상 양수이므로 위 식이 성립함을 알 수 있습니다.

보통 물리학이나 통계학에서 자주 사용되는 가우스 적분은 다음과 같은 형태입니다.

$$
\int_{-\infty}^\infty e^{-\frac{a}{2}y^2} dy = (2\pi)^{\frac{1}{2}} a^{-\frac{1}{2}}
$$

<br/>

### 2) Generalize 1D Gaussian Integral

$$
(2\pi)^{-\frac{1}{2}}\int_{-\infty}^\infty e^{-\frac{1}{2}a x^2 + Jx} = a^{-\frac{1}{2}} e^{\frac{J^2}{2a}}
$$

> 단순히 완전제곱식을 이용하여 정리하면 해결되는 적분입니다.
> $$\int_{-\infty}^\infty e^{-\frac{a}{2}(y - \frac{J}{a})^2 + \frac{J^2}{2a}} = \int_{-\infty}^\infty e^{-\frac{a}{2}t^2} dt \cdot e^{\frac{J^2}{2a}} = (2\pi)^{\frac{1}{2}} a^{-\frac{1}{2}} e^{\frac{J^2}{2a}}$$

-----

## 🐪 단변수 가우시안 (Single variate Gaussian)

![Single variate Gaussian](/posts/images/single.png)
