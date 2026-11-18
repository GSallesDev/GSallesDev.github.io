---
layout: post
title: "Renderizacao de iluminacao em sprites 2d"

categories: [Notes, GameDev]
tags: [gamedev]

math: true
---
No atual motor para jogos de corrida que desenvolvo, VorteX, uso uma técnica de renderização para atingir uma iluminação dinâmica para os carros.

<p align="center">
<img src="{{ site.baseurl }}/assets/images/vortex/2026-11-17-screenshot0.png">
</p>

Em buffers são renderizadas as normais do sprite, onde cada componente RGB, representa uma direção no espaço tridimensional. O objetivo do mesmo segue da formula da iluminação difusa de Lambertiana.

$$
I_d = k_d \cdot I_l \cdot \max(0, \mathbf{N} \cdot \mathbf{L})
$$

A intensidade da luz $$I_{d}$$ é computado em termos do produto entre o coeficiente difuso $$k_{d}$$, a intensidade da fonte da luz $$I_{l}$$ e o produto escalar entre a normal $$N$$ e a direção da luz $$L$$, limitada a ser positiva ou igual a zero.

<p align="center">
<img src="{{ site.baseurl }}/assets/images/vortex/2026-11-17-normal-render.png">
</p>

Este buffer passa por um shader que transforma as coordenadas em relação ao mundo, de acordo com a rotação $$\theta$$ do objeto representada pela matrix $$R(\theta)$$.

$$
N' = R(\theta)N = \begin{bmatrix}\cos \theta & -\sin \theta \\ \sin \theta & \cos \theta\end{bmatrix}\begin{bmatrix} n_{x} \\ n_{y}\end{bmatrix} = \begin{bmatrix} n_{x}\cos\theta-n_{y}\sin\theta \\ n_{x}\sin\theta+n_{y}\cos\theta\end{bmatrix}
$$

Formando a nova normal $$N'$$, Este é a normal que será alimentada no nosso modelo de iluminação, aplicado sob o buffer de cores do sprite.

<p align="center">
<img src="{{ site.baseurl }}/assets/images/vortex/2026-11-17-screenshot-color.png">
</p>

Assim formando a imagem final

---

Se deseja saber mais ou acompanhar, considere ver o Projeto [Vortex](https://github.com/GSallesDev/VorteX) no meu github.

Espero que tenha gostado.

Obrigado por ler. 

---

© Gustavo Henrique de Sales Silva. Todos os direitos reservados.
