---
layout: post
title: "Divisibilidade como conjunto"

categories: [Notes, Math]
tags: [mathematics]

math: true
---

Uma propriedade interessante dos números inteiros, observe, estes são os múltiplos de $$2$$.
$$
\cdots -8, -6, -4, -2, 0, 2, 4, 6, 8, \cdots
$$
Estes são múltiplos de $$8$$
$$
\cdots -16, -8, 0, 8, 16 \cdots 
$$
Percebe-se que todos os múltiplos de $$8$$, também são múltiplos de $$2$$. E esta propriedade que vamos explorar hoje, e se ela generaliza para quaisquer anéis.

Todos os múltiplos inteiros de $$d \in \mathbb{Z}$$, denotados como $$d\mathbb{Z}$$ ou $$(d)$$, chamado de ideal de $$d$$, é definido como:

$$
d\mathbb{Z}= \left\{dk \bigm| k \in \mathbb{Z}\right\} = (d)
$$
Propomos:

$$
2 | 8 \iff 8\mathbb{Z} \subseteq 2\mathbb{Z}
$$
---

Vamos explorar esta propriedade.
Se temos que 
$$
d|n \iff (n) \subseteq (d), \qquad \boxed{n\mathbb{Z} \subseteq d\mathbb{Z}}
$$
Isto é, $$d$$ divide $$n$$ se e somente se o ideal gerado por $$n$$, for um subconjunto do ideal gerado por $$d$$.

Esta seria uma perspectiva interessante de se observar a divisão, assim a generalizando em uma propriedade mais ampla. 

Mas primeiramente vamos a provar a proposição.
Na direção $$d|n \implies (n) \subseteq (d)$$

Suponha que $$d$$ divide $$n$$ e $$a$$ é um elemento do ideal gerado por $$n$$. Provar $$a$$ é um elemento gerado pelo ideal de $$d$$ provaria a suposição.
Pela definição, $$d$$ dividir $$n$$ implicaria a existência de um numero $$k \in \mathbb{Z}$$ tal que $$n = dk$$.
E $$a$$ ser um elemento gerado pelo ideal de $$n$$, implicaria existir um numero $$l \in \mathbb{Z}$$, tal que $$a = nl$$
Então assim $$a = dkl \in (d)$$ $$\square$$

Agora inversamente, $$(n) \subseteq (d) \implies  d|n$$

Suponha que $$(n) \subseteq (d)$$, o que implica que $$n \in (n) \subseteq (d)$$

Um tanto quanto verboso, mas em suma, se o ideal gerado por $$n$$ é um subconjunto do ideal gerado por $$d$$, poderíamos afirmar que $$n$$ é um elemento de do ideal gerado por $$n$$, que é um subconjunto de $$d$$.

Então $$n \in (d)  \implies n = dk, \quad k \in \mathbb{Z}$$
Então $$n$$, é um elemento do ideal gerado por $$d$$, o que implica que existe um numero $$k \in \mathbb{Z}$$ tal que $$n = dk$$

Ou seja, $$d$$ divide $$n$$, por definição. $$\square$$

---

É uma implicação interessante, e cria uma conexão um tanto quanto inesperada.  

Mas exploremos outras propriedades, observe.
Seja $$I$$ o ideal gerado por $$d$$
Se temos dois elementos $$a$$ e $$b$$ em $$I$$, então quaisquer operações de soma e/ou subtração, também estarão em $$I$$ 
Isto é, $$I$$ é fechado sob soma e subtração.

Pois se $$a, b$$ são elementos de  $$I$$ então $$a = dk$$ e $$b = dl$$ para $$k, l \in \mathbb{Z}$$
Então $$a \pm b = d(k \pm l) \in (d)$$ i.e. $$(I)$$ $$\square$$

A segunda propriedade é
Se $$a$$ é um elemento de $$I$$, então para quaisquer $$n \in \mathbb{Z}$$, $$a \cdot n$$ também estará em $$I$$.
Ou seja, $$a$$ possui uma propriedade de absorção na multiplicação com números inteiros.
Pois $$a = dk, \quad k \in \mathbb{Z}$$ e então $$an = d(kn) \in I$$ $$\square$$

Se escolhermos um subconjunto abstrato dos números inteiros que obedecem a estas duas condições, ele se chamará de ideal.
Estão são as propriedades características de um ideal.

---

Então propõem-se o teorema:
Se $$I \subseteq \mathbb{Z}$$ é um conjunto que satisfaz estas propriedades, então $$I = (d)$$ para algum $$d \in \mathbb{Z}$$

Analisemos os casos possíveis, o mais trivial, caso $$I = \{0\}$$ então $$I$$ é o ideal gerado por $$0$$.

Para os outros casos
Seja $$d = \min(I \cap \mathbb{N})$$

> Prova que $$\min(I \cap \mathbb{N})$$ existe
> Seja $$d \in \mathbb{Z}$$ com $$d \neq 0$$
> $$I = d\mathbb{Z} = \{dk \bigm| k \in \mathbb{Z}\}$$
> $$\mathbb{N} = \mathbb{Z}^{>0}$$
> Se $$d > 0$$, tomando $$k = 1 \in \mathbb{Z}$$, temos $$d \cdot 1 = d \in I$$, como $$d$$ é um inteiro positivo, $$d \in I \cap \mathbb{N}$$
> Se $$d < 0$$, tomando $$k = -1 \in \mathbb{Z}$$, temos $$d \cdot (-1) = -d \in I$$, como $$-d$$ é um inteiro positivo. $$-d \in I \cap \mathbb{N}$$
> Em ambos casos, $$I \cap \mathbb{N}$$ é um subconjunto não vazio de $$\mathbb{N}$$, Pelo principio da boa ordenação, existe $$\min(I \cap \mathbb{N})$$
> $$\square$$ 

Pegue um valor $$n$$ em $$I$$

Pelo algoritmo da divisão, existem $$k, r \in \mathbb{Z}$$, tais que $$n = dk + r$$, $$0 \le r < d$$
Como $$d \in I$$ e $$k \in \mathbb{Z}$$, segue a propriedade de absorção $$dk \in I$$. E como $$n \in I$$ e $$dk \in I$$, o fechamento de $$I$$ sob subtração garante que $$r = n - dk \in I$$.

Suponha que $$r \neq 0$$, então $$0 < r < d$$, o que implica que $$r \in \mathbb{N}$$, e portanto, $$r \in I \cap \mathbb{N}$$, contudo, $$r < d$$, contrariaria a minimalidade de $$d = \min(I \cap \mathbb{N})$$, Logo $$r = 0$$ de modo que $$n = dk \in (d)$$ $$\square$$, logo $$I \subseteq (d)$$ $$\square$$

e inversamente, por definição, $$d = \min(I \cap \mathbb{N})$$, garante que $$d \in I$$. Pegue um elemento arbitrário $$x \in (d)$$, por definição de $$(d)$$, existe $$k \in \mathbb{Z}$$ tal que $$x = dk$$
Como $$d \in I$$, e $$k \in Z$$, a propriedade de absorção garante que $$dk \in I$$, ou seja, $$x \in I$$, logo $$(d) \subseteq I$$ $$\square$$

Ambas em complemento, concluímos que $$I = (d)$$ $$\blacksquare$$

---

Continuaremos a explorar estas ideias e suas implicações em próximas publicações.

Espero que tenha gostado.

Obrigado por ler. 

---

© Gustavo Henrique de Sales Silva. Todos os direitos reservados.
