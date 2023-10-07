## Imparare dagli esempi
### Step base
1. **Osservo il fenomeno**
	- Scatto delle instantanee del fenomeno detti **esempi**
2. **Rappresentazione dei dati**
	- Rappresento gli esempi **numericamente**
	- Rimuovo *feature* inutili
3. Scelgo un **algoritmo**
4. **Verifica dei risultati**
### Formalizzazione
Prendo:
- $\mathbb{X}\subseteq\mathbb{R}^d$: Insieme di **input**
- $\mathbb{Y}\subseteq\mathbb{R}$: Insieme di **output**

Assumo che esista $p_{X,Y}(\vec{x}, y)$ su $\mathbb{X}\times\mathbb{Y}$ sconosciuta che genericamente è data da:
$$
p_{X,Y}(\vec{x}, y) = p_X(\vec{x})\cdot p_Y(y|\vec{x})
$$
In accordo con questa probabilità genero un **training set**:
$$
S=\{(\vec{x_i},y_i)\in\mathbb{X}\times\mathbb{Y}:i=1...l\}
$$
pescando $l$ volte nel set $\mathbb{X}\times\mathbb{Y}$.

L'**obiettivo** diventa quindi trovare una $f_s:\mathbb{X}\rightarrow\mathbb{Y}$ con $f_s\in \mathbb{H}$ (**Spazio delle ipotesi**) tale che per ogni $\vec{x}\in\mathbb{X}$ è in grado di predire la corrispettiva $y\in\mathbb{Y}$ ossia $f_s(\vec{x})\sim y$
### Classificazione algoritmi ML
- Se **non** utilizzo le etichette l'algoritmo prende il nome di **algoritmo non supervisionato**
- Se utlizzo le etichette l'algorittmo prende il nome di **algoritmo supervisionato** e si distingue in:
	- **Alg. Classificazione Binaria** se $\mathbb{Y} = \{y_1, y_2\}$ 
	- **Alg. Classificazione Multipla** se $\mathbb{Y} = \{y_1,...,y_p\}$
	- **Alg. Regressione** se   $\mathbb{Y} = \mathbb{R}$