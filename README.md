# ✈️ Recomendação de Viagem (Similaridade do Cosseno)

---

## 🎯 Visão Geral

Este sistema é um **Assistente de Viagem** que implementa um modelo de **Recomendação Baseada em Conteúdo** (Content-Based Filtering). O mecanismo centraliza-se na **Similaridade do Cosseno** para quantificar a semelhança entre as características de um destino e as preferências de viagem de um usuário.

---

## 💡 Metodologia: A Álgebra da Similaridade

O cálculo da similaridade é a etapa mais crítica. Primeiramente, as preferências categóricas (Tipo, Duração, Estação, Interesse) são convertidas em **vetores numéricos** usando **One-Hot Encoding**.

### 1. Representação Vetorial

Cada destino ($D$) e as preferências do usuário ($U$) são representados como vetores no mesmo espaço multidimensional:

$$\text{Destino} = D = [d_1, d_2, d_3, \dots, d_n]$$
$$\text{Usuário} = U = [u_1, u_2, u_3, \dots, u_n]$$

Onde $n$ é o número total de características únicas (ex: $d_i = 1$ se o Destino é 'Praia', $d_i = 0$ caso contrário).

### 2. O Cálculo da Similaridade do Cosseno

A Similaridade do Cosseno mede o **cosseno do ângulo** ($\theta$) entre os vetores $D$ e $U$. Quanto mais próximo de 1, mais alinhados estão os vetores (maior similaridade).

A fórmula algébrica é dada pelo **produto escalar** dos vetores dividido pelo produto de suas **magnitudes (normas)**:

$$\text{Similaridade}(D, U) = \cos(\theta) = \frac{D \cdot U}{\|D\| \|U\|}$$

Expandindo o cálculo:

$$\text{Similaridade}(D, U) = \frac{\sum_{i=1}^{n} d_i u_i}{\sqrt{\sum_{i=1}^{n} d_i^2} \sqrt{\sum_{i=1}^{n} u_i^2}}$$

### 3. Aplicação

O resultado é um score que indica a correspondência:

* **Score = 1:** Similaridade Perfeita (ângulos $0^{\circ}$). O destino corresponde exatamente às preferências.
* **Score = 0:** Ângulos de $90^{\circ}$. Sem similaridade (os vetores não têm características em comum).
* **Score < 1:** Similaridade Parcial (o mais comum).

O destino com a maior pontuação de similaridade é o recomendado.

---

## 📊 Resultados e Recomendações (Exemplo)

| Preferência do Usuário | Destino Recomendado | Score de Similaridade |
| :--- | :--- | :--- |
| Praia, Relaxamento, Verão | **Cancun / Búzios** | **1.0000 (Perfeita)** |
| Cultural, História, Outono | **Kyoto / Machu Picchu** | **0.7071 (Forte)** |

---

### 💻 Tecnologias

* `Python`
* `Pandas` (One-Hot Encoding)
* `Scikit-learn` (`cosine_similarity`)

