# Unlinked-regression

This repository is related to the work (link to the article).
It contains a description of the data generation algorithm for numerical experiments and the code for these experiments.

## Data Generation Algorithm
Let $\mathcal{G}(F, G, a, n, z)$ denote the data generation algorithm of size $n$ for the model $Y = aX + \varepsilon$, in which the random variables $X$ and $\varepsilon$ are independent and have distributions $F$ and $G$, respectively, and for this dataset $l(n) = \left[z \cdot n \right]$, where $z \in [0, 1]$.

Generation algorithm.

Set $n_d = \left[z \cdot n \right]$, $n_i = n - n_d$. The algorithm $\mathcal{G}(F, G, a, n, z)$ is structured as follows:

1. Generation of pairs:

- From the distribution $F$, generate $n_d$ independent random variables $X_j$;
- From the distribution $G$, independently of the $X_j$ obtained in the previous step, generate $n_d$ independent random variables $\varepsilon_j$;
- Construct a sample of size $n_{dep}$ using the formula $Y_j = aX_j + \varepsilon_j$.

2. Generation of random variables without pairs:

- From the distribution $F$, independently of everything else, generate $n_i$ independent random variables $\widetilde{X}_j$;
- From the distribution $G$, independently of everything else, generate $n_i$ independent random variables $\widetilde{\varepsilon}_j$;
- Construct a sample of size $n_i$ using the formula $Y_j = a\widetilde{X}_j + \widetilde{\varepsilon}_j$;
- From the distribution $F$, independently of everything else, generate $n_i$ independent random variables $X_j$.

3. Combine the $\{X_i\}$ obtained in steps (1) and (2) and shuffle them randomly. Do the same for $\{ Y_i \}$.


