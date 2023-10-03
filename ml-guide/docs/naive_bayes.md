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

