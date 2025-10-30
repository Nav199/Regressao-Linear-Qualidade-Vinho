# 🍷 Regressão Linear para Predição da Qualidade de Vinho Branco

## 📝 Descrição do Projeto

Este projeto utiliza um modelo de **Regressão Linear Múltipla** (utilizando `scikit-learn`) para prever a **qualidade (score)** de vinhos brancos, com base em suas 11 características físico-químicas.

O objetivo é:
1.  Modelar a relação entre os componentes químicos (como acidez, álcool e dióxido de enxofre) e a nota de qualidade.
2.  Avaliar a capacidade preditiva de um modelo linear para esta tarefa.

## ⚙️ Tecnologias Utilizadas

* **Python**
* **Pandas** (Manipulação de dados)
* **Scikit-learn** (Modelo de Regressão Linear e Métricas)
* **Seaborn** e **Matplotlib** (Visualização de dados)

## 📊 Análise Exploratória e Resultados

### 1. Estatísticas Descritivas (`wines.describe()`)

O conjunto de dados possui 4898 observações. A variável alvo (`quality`) tem uma média de **5.87** e varia de 3 a 9.


### 2. Mapa de Correlação

O mapa de calor ilustra as relações lineares entre as variáveis.

* **Correlacionadas Positivamente com a Qualidade:** O `alcohol` (Álcool) é a variável com a correlação positiva mais forte com a qualidade.
* **Correlacionadas Negativamente com a Qualidade:** A `volatile acidity` (Acidez Volátil) e a `density` (Densidade) mostram forte correlação negativa.


### 3. Coeficientes do Modelo (`lr.coef_`)

Após o treinamento, o modelo de Regressão Linear estabeleceu os seguintes coeficientes para a equação, que indicam a magnitude e direção da influência de cada variável na previsão da qualidade.

| Variável | Coeficiente (Peso) |
| :--- | :--- |
| `fixed acidity` | $9.46658 \times 10^{-2}$ |
| `volatile acidity` | **$-1.82543 \times 10^0$** |
| `citric acid` | $3.07827 \times 10^{-3}$ |
| `residual sugar` | $1.04348 \times 10^{-1}$ |
| `chlorides` | $-2.77044 \times 10^{-1}$ |
| `free sulfur dioxide` | $4.17726 \times 10^{-3}$ |
| `total sulfur dioxide` | $8.34206 \times 10^{-5}$ |
| `density` | **$-2.23683 \times 10^2$** |
| `pH` | $7.91866 \times 10^{-1}$ |
| `sulphates` | $7.40460 \times 10^{-1}$ |
| `alcohol` | **$1.05663 \times 10^0$** |

**Principais Insights dos Coeficientes:**
* **Influência Negativa:** A **`density`** e a **`volatile acidity`** possuem os maiores impactos negativos na qualidade.
* **Influência Positiva:** O **`alcohol`** e o **`pH`** (seguido por `sulphates`) são os principais impulsionadores positivos da qualidade.

### 4. Avaliação do Modelo

A performance do modelo foi avaliada no conjunto de teste (`X_test`).

| Métrica | Valor |
| :--- | :--- |
| **Mean Squared Error (MSE)** | **0.5866** |

Um MSE de **0.5866** indica o erro médio quadrado entre as previsões e os valores reais. Considerando que a escala de qualidade tem um desvio padrão de **0.88** (conforme `wines.describe()`), o modelo possui uma capacidade preditiva razoável, mas pode ser melhorado com a exploração de modelos não-lineares.

### 5. Gráfico de Predição vs. Realidade

O gráfico de dispersão compara os valores de qualidade reais (`valores esperados`) com os valores gerados pelo modelo (`valores preditos`).


**Interpretação:**
A dispersão vertical em cada valor esperado mostra o erro do modelo. Observa-se que o modelo consegue prever a tendência central (média) de cada nível de qualidade, mas tem dificuldades em acertar o valor exato, o que é típico em problemas de regressão onde a variável alvo é discreta (como a nota de qualidade).

---
*Desenvolvido como projeto de Machine Learning e Análise de Dados.*
