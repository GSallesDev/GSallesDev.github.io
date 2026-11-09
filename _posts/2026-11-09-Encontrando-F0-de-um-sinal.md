---
layout: post
title: "Encontrando F0 de um sinal"

categories: [Notes, Math]
tags: [mathematics]

math: true
---
Estudo há um tempo aspectos da síntese de voz cantada, inspirado em alguns UTAUs, comecei a implementar um pequeno sistema TD-PSOLA, e um dos aspectos fundamentais do mesmo é a determinação da F0 do sample do voice-bank. 

E para este existe um método interessante, imagine uma sinal contínuo, para exemplo, usemos uma onda puramente periódica, sendo a frequência o inverso do período, e o período, a menor translação da função que deixe-a exatamente como era.
![Função Periódica](assets/images/posts/2026-11-09-wave-function-period-frequency.png)


Entretanto, uma direta comparação seria equívoca, pois sinais exatamente auto-semelhantes são um restrito subconjunto de todos os sinais possíveis. Um simples decaimento exponencial já é o suficiente para esta técnica ser sub-ótima.

Então, poderíamos calcular o produto entre a função e ela mesma, movida com pequeno desvio $$\tau$$ em um tempo $$t$$.
$$
\sum_{n} f(x)f(x + \tau)
$$
O lugar com o maior valor, seria o lugar mais auto-similar, por tanto, o $$\tau$$ que define a frequência fundamental. Entretanto, devemos limitar a um subconjunto de samples do sinal original, representado por uma janela $$W$$
Assim a função de auto-correlação, é definida:
$$\text{ACF}(\tau, t) = \sum^{t + W}_{n = t} f(x_{n})f(x_{n} + \tau)$$
Entretanto, o problema permanece, e a fundamental pode ser incorretamente prevista. Em casos como:
![Função Periódica](assets/images/posts/2026-11-09-wave-function-exp-decai.png)

Para este caso podemos explorar uma propriedade interessante, como a definição de $$\tau$$ é  caracterizada por:
$$
f(x) - f\left(x + \tau\right) = 0 \quad \forall x
$$
Podemos, então observar que a função da diferença, quanto mais similar, mais próximo de zero, esta equação será, então a soma sob determinada janela, também o será.
$$
\sum^{t + W}_{n = t} f(x_{n}) - f\left(x_{n} + \tau\right)
$$
Porém, valores negativos podem influenciar o resultado, para contornar isto, então elevamos ao quadrado os operandos. 
$$
\text{DF}(\tau, t) = \sum^{t + W}_{n = t} \left(f(x_{n}) - f(x_{n} + \tau)\right)^{2}
$$
E chegamos a função da diferença do sinal, e observe algo interessante, o mesmo pode ser definido em termos da auto-correlação. Sendo na implementação, mais pratico.
$$
\text{DF}(\tau, t) = \text{ACF}(0, t) + \text{ACF}(0, t + \tau) - 2 \cdot 
\text{ACF}(\tau, t)
$$
Deste, procuramos o minimo. Entretanto, múltiplos inteiros de F0, ainda podem ser falsamente detectados, já que estes pontos representam os pontos de auto semelhança, e para isto corrigir usamos:
$$
\text{CMNDF}(\tau) = \frac{\text{DF}(\tau)}{\frac{1}{\tau} \sum^{\tau}_{j=1} \text{DF}(j)}
$$
Que é a normalização da função da diferença. Ou melhor,
$$
\text{CMNDF}(\tau) = \begin{cases} 1 & \tau = 0 \\ \frac{\text{DF}(\tau)}{\frac{1}{\tau} \sum^{\tau}_{j=1} \text{DF}(j)} & \tau > 0\end{cases}
$$


---
Fiz uma pequena implementação do CMNDF, utilizando FFT
https://github.com/GSallesDev/CS/blob/main/math/signal/cmndf.py

Espero que tenha gostado.

Obrigado por ler. 

---

© Gustavo Henrique de Sales Silva. Todos os direitos reservados.
