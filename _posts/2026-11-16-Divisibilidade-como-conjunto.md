---
layout: post
title: "Divisibilidade como conjunto"

categories: [Notes, Math]
tags: [mathematics]

math: true
---

Este são os múltiplos de 2
Estes são os múltiplos de 8
Todos múltiplos múltiplos de 8, também são múltiplos de 2.
$$2 | 8 \iff 4\mathbb{Z} \subseteq 2\mathbb{Z}$$
Escrever divisibiidade, $\text{mdc}$, $\text{mmc}$ e números primos, em termos de conjuntos.
Esta definição generaliza para quaisquer anéis.

Para $d \in \mathbb{Z}$
$$d\mathbb{Z}= \left\{dk \bigm| k \in \mathbb{Z}\right\} = (d)$$
$(d)$ representa todos múltiplos inteiros de $d$
NOTA: $(0) = \{0\}$, então $0|0$, $\exists m$

proposição:
$$d|n \iff (n) \subseteq (d), \qquad \boxed{n\mathbb{Z} \subseteq d\mathbb{Z}}$$
Prova:
Primeira direção: $d|n \implies (n) \subseteq (d)$
Suponha que $d|n$ e $a \in (n)$. Provar $a \in (d)$ provaria a suposição.
Pela definição
$d|n \implies n = dk, \quad k \in \mathbb{Z}$
$a \in (n) \implies a = nl, \quad l \in \mathbb{Z}$
$\therefore a = dkl \in (d)$
$\square$

Agora inversamente.
Primeira direção: $(n) \subseteq (d) \implies d|n$
Suponha que $(n) \subseteq (d)$, $\implies n \in (n) \subseteq (d)$
então $n \in (d)  \implies n = dk, \quad k \in \mathbb{Z}$
$\therefore n = dk \implies d|n$
$\square$

---
Seja $I = (d)$
prop.: Se $a, b \in I$, então $a \pm b \in I$
prova:
Se $a, b \in I$ então $a = dk, b = dl, \quad k, l \in \mathbb{Z}$
Então $a \pm b = d(k \pm l) \in I$
$\square$

prop. Se $a \in I$ e $n \in \mathbb{Z}$ então $an \in I$
$a = dk, \quad k \in \mathbb{Z}$
$an = d(kn) \in I$
$\square$

* $(d)$ é fechado sob a soma e subtração

Se escolhermos um subconjunto abstrato dos números inteiros que obedecem a estas duas condições, ele se chamará de ideal.
Estão são as propriedades características de um ideal.

---
Demonstrar que esta é a correta generalização,
Teorema: Se $I \subseteq Z$ é um conjunto que satisfaz estas propriedades, então $I = (d)$ para algum $d \in \mathbb{Z}$
prova:
Caso $I = \{0\} \implies I = (0)$
Caso $I \neq \{0\}$
Seja $d = \min(I \cap \mathbb{N})$

> Prova que $\min(I \cap \mathbb{N})$ existe
> Seja $d \in \mathbb{Z}$ com $d \neq 0$
> $I = d\mathbb{Z} = \{dk \bigm| k \in \mathbb{Z}\}$
> $\mathbb{N} = \mathbb{Z}^{>0}$
> Se $d > 0$, tomando $k = 1 \in \mathbb{Z}$, temos $d \cdot 1 = d \in I$, como $d$ é um inteiro positivo. $d \in I \cap \mathbb{N}$
> Se $d < 0$, tomando $k = -1 \in \mathbb{Z}$, temos $d \cdot (-1) = -d \in I$, como $-d$ é um inteiro positivo. $-d \in I \cap \mathbb{N}$
> Em ambos casos, $I \cap \mathbb{N}$ é um subconjunto não vazio de $\mathbb{N}$, Pelo principio da boa ordenação, existe $\min(I \cap \mathbb{N})$
> $\square$

pegue $n \in I$
Pelo algoritmo da divisão, existem $k, r \in \mathbb{Z}$, tais que $n = dk + r$, $0 \le r < d$
Como $d \in I$ e $k \in \mathbb{Z}$, segue a propriedade de absorção $dk \in I$. E como $n \in I$ e $dk \in I$, o  fechamento de $I$ sob subtração garante que $r = n - dk \in I$
Suponha que $r \neq 0$, então $0 < r < d$, o que implica que $r \in \mathbb{N}$, e portanto, $r \in I \cap \mathbb{N}$, Contudo, $r < d$, contrariaria a minimalidade de $d = \min(I \cap \mathbb{N})$, Logo $r = 0$ de modo que $n = dk \in (d)$ $\square$
$\therefore I \subseteq (d)$

e inversamente:
Por definição, $d = \min(I \cap \mathbb{N})$, garante que $d \in I$
Peque um elemento arbitrário $x \in (d)$, por definição de $(d)$, existe $k \in \mathbb{Z}$ tal que $x = dk$
Como $d \in I$, e $k \in Z$, a propriedade de absorção garante que $dk \in I$, ou seja, $x \in I$ $\square$
$\therefore (d) \subseteq I$

Das duas inclusões concluímos que $I = (d)$

---

$(a) + (b) = \{ax + by \bigm| x, y \in \mathbb{Z}\}$

Proposição: $(a) + (b) = (\text{mdc}(a, b))$

Talvez valesse um pouco mais de rigor, mas
para $a, b \in \mathbb{Z}$, segundo a definição clássica $d = \text{mdc}(a, b) \in \mathbb{Z}$, então $(\text{mdc}(a, b))$ responde as propriedades do teorema.

-> $(a) + (b) = (d)$
Para o numero $d$ ser o $\text{mdc}$, ele primeiramente necessita ser um divisor comum.
Observe
Basta $y=0$
$(a) \subseteq (a) + (b) = (d) \implies (a) \subseteq (d) \implies  d|a$
$(b) \subseteq (a) + (b) = (d) \implies (b) \subseteq (d) \implies  d|b$
Então $d$ é um divisor comum de $a$ e $b$.

Suponha que $c | a$ e $c | b$
> Equivale a $a \in (c)$ e $b \in (c)$
> Pela propriedade de absorção, temos que $ax \in (c)$ e $by \in (c)$ para quaisquer Pelo fechamento sob adição concluímos que $ax + by \in (c)$
-> $c | (ax + by) \quad \forall x, y \in \mathbb{Z}$

Pegue $u, v \in \mathbb{Z}$, tais que $au + bv = d$, aplicando $c | (ax + by) \quad \forall x, y \in \mathbb{Z}$
-> $c|d$
> Se $c|d$ e $d > 0$, então $c \le d$

Logo $d$ é o $\text{mdc}$

$d|n$, $(n) \subseteq (d)$
$\text{mdc}(a, b)$, $(a) + (b)$
$\text{mmc}(a, b)$, $(a) \cap (b)$
$a \cdot b$, $(a)(b) = (ab)$

---
 Noção de um números primos.


