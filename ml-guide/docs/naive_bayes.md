# Naive Bayes Classifier

> **Bayes Rule**
> $$
> p_Y(y_i|\vec{x}) = \frac{p_X(\vec{x}|y_i)\cdot p_Y(y_i)}{p_x(\vec{x})}
>$$
> con:
> $$
> p_x(\vec{x}) = \sum_{i=1}^l{p_X(\vec{x}|y_i)\cdot p_Y(y_i)}
> $$

Stimare $p_Y(y_i)$ non è difficile (basta "contare" nel **training set**), al contrario $p_X(\vec{x}|y_i)$ (**verosimiglianza**) richiede uno sforzo maggiore (nel caso discreto potrei "contare" anche in questo caso).

## Massima verosimiglianza
- Pongo $p(\vec{x}|y_i)\rightarrow p(\vec{x}|y_i,\vec{\theta_i})$ con $\vec{\theta_i}$ i parametri di una distribuzione probabilistica nota
- Suppungo **IID** fra gli esempi, per cui $\vec{x}$ etichettato $y_i$ non ci da info su $\vec{\theta_j}$ con $j\neq i, \forall \vec{x}\in S$ per cui posso lavorare "classe per classe" (da ora in poi con $S$ indichiamo i sample di una classe fissata):

$$
p(S|\vec{\theta}) = \prod_{k=1}^np(\vec{x_k}|\vec{\theta})
$$
> **Massima verosimiglianza**
> Definita $p(S|\vec{\theta})$ verosimiglianza rispetto a tutti gli esempi, $\hat{\vec{\theta}}$ è la massima verosimiglianza di $\vec{\theta}$ se massimizza $p(S|\vec{\theta})$

## Classificatore di Bayes ottimale
$$
f(x) = \arg\max_{c\in Y}p(y=c|x)=\arg\max_{c\in Y}\phi_c(x)\pi_c
$$
Con:
- $\phi_c(x) = p(x|y_c)$ la **verosimiglianza**
- $\pi_c$ la probabilità a priori (**prior**)

## Classificatore di Bayes naive
> **Stimatore di verosimiglianza naive**
> $$
> P(x^1,x^2, ...,x^k|y_c) = \prod_{i=1}^kp(x^i|y_c)
> $$
> A parole supponiamo che le feature del singolo esempio siano indipendenti

$$
\phi_c=p(X=x|Y=c) = \prod_{d=1}^kp(X^d=x^d|Y=c)=\prod_{d=1}^k\phi_{cd}(x^d)
$$
Il nostro classificatore diventa quindi:
$$
f(x) = \arg\max_{c\in Y}\pi_c\prod_{d=1}^k\phi_{cd}(x^d)
$$
Con $\phi_c(x)$ modellata con una distribuzione probabilistica nota:
- **Normale** per il caso reale
- **Bernoulli** per il caso binario
- **Categorica** per il caso multiclasse

### Stimatore con normale
> **Normale nel caso 1D**
> $$
> \mathcal{N}(x^d,\mu_{cd},\sigma_{cd}) = \frac{1}{\sqrt{2\pi\sigma_{cd}^2}}\exp{(-\frac{1}{2\sigma_{cd}^2}(x^d-\mu_{cd})^2)}
> $$

$$
\pi_c = \frac{1}{n}\sum_{i=1}^n[y_i=c]
$$
A parole, conta quante volte appare la classe $c$

Nel caso utilizzi la normale ho due parametri:
$$
\mu_{cd} = \frac{\sum_{i=1}^n[y_i=c]x_i^d}{\sum_{i=1}^n[y_i=c]}
$$
e

$$
\sigma_{cd} = \frac{\sum_{i=1}^n[y_i=c] (x_i^d-\mu_{cd})}{\sum_{i=1}^n[y_i=c]}
$$