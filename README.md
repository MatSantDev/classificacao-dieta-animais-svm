# Classificação da Dieta de Animais com SVM

> **Projeto acadêmico** desenvolvido para o **Summit 2026**.

[![Abrir no Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/MatSantDev/classificacao-dieta-animais-svm/blob/main/ProjetoSummit.ipynb)

## Sobre o projeto

Este é um trabalho acadêmico de aprendizado de máquina. O objetivo é usar um
modelo **SVM (Support Vector Machine)** para prever a **dieta** de um animal a
partir das suas características físicas e comportamentais, classificando-o em
uma de três categorias:

- 🌿 **Herbívoro**
- 🥩 **Carnívoro**
- 🍽️ **Onívoro**

## Grupo

- Mateus Santos
- Antonio Fonseca

## Dataset

Foi usado o [Zoo Animal Classification](https://www.kaggle.com/datasets/uciml/zoo-animal-classification)
(UCI / Kaggle), com **101 animais** e **16 características** (pelos, penas,
ovos, leite, dentes, nadadeiras, número de patas etc.), sem valores nulos.

O dataset original não informa a dieta, então **cada animal foi rotulado
manualmente** e essa informação foi adicionada na coluna `diet`.

## O que o notebook faz

1. **Carrega** o dataset com `kagglehub`.
2. **Rotula** a dieta de cada animal.
3. **Explora** os dados: formato, tipos, estatísticas, valores nulos,
   distribuição das dietas (que é desbalanceada) e matriz de correlação.
4. **Prepara** os dados: remove `animal_name` e `class_type`, separa 80% para
   treino e 20% para teste e normaliza com `StandardScaler`.
5. **Compara** os kernels do SVM (linear, poly, RBF e sigmoid). Os quatro
   empatam em **71,43%** de acurácia.
6. **Otimiza** os hiperparâmetros com `GridSearchCV`. A melhor combinação foi
   `kernel='sigmoid'`, `C=10`, `gamma=0.1`.
7. **Avalia** o modelo final no conjunto de teste, com relatório de
   classificação e matriz de confusão.

## Resultados

| Dieta     | Acertos |
|-----------|---------|
| Herbívoro | 4 de 4  |
| Carnívoro | 12 de 13 |
| Onívoro   | 0 de 4  |
| **Total** | **16 de 21 (76,2%)** |

O modelo acerta bem herbívoros e carnívoros, mas erra todos os onívoros
(por exemplo esquilo, mosquito, javali e gaivota). Isso acontece porque há
poucos onívoros no dataset e porque as características físicas deles se
parecem com as das outras duas classes.

## Arquivos

| Arquivo | Descrição |
|---------|-----------|
| [`ProjetoSummit.ipynb`](ProjetoSummit.ipynb) | Notebook com todo o código e as análises |
| [`Classificação da Dieta de Animais com SVM.pptx`](Classificação%20da%20Dieta%20de%20Animais%20com%20SVM.pptx) | Slides da apresentação no Summit 2026 |
| [`LICENSE`](LICENSE) | Licença MIT |

## Como executar

Clique no botão **Abrir no Colab** acima, ou rode localmente:

```bash
pip install pandas matplotlib seaborn scikit-learn kagglehub jupyter
jupyter notebook ProjetoSummit.ipynb
```

## Tecnologias

Python · pandas · scikit-learn · matplotlib · seaborn · kagglehub · Google Colab

## Licença

Distribuído sob a licença MIT. Veja [`LICENSE`](LICENSE).
