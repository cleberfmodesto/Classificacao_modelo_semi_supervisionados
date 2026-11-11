# Classificação com aprendizado semi-supervisionado

Como construir classificadores úteis quando apenas parte dos dados tem rótulos? Este projeto explora essa questão com dois exemplos práticos: classificação da qualidade do leite e uma atividade de classificação com dados de diabetes.

[![Abrir aula no Google Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/cleberfmodesto/Classificacao_modelo_semi_supervisionados/blob/main/Aulas/Aula%2B5%2B-%2BAprendizado%2Bsemi-supervisionado.ipynb)


## O problema

Em muitos projetos, obter rótulos para todos os exemplos exige tempo e conhecimento especializado. O aprendizado semi-supervisionado busca aproveitar também os dados sem rótulo, combinando-os com os exemplos já classificados para melhorar o treinamento de um modelo.

Os notebooks aplicam essa ideia a dois cenários: estimar a qualidade de amostras de leite e classificar registros de um conjunto de dados de diabetes. O segundo caso é exclusivamente didático e não deve ser usado para diagnóstico ou decisões clínicas.

## A solução

O projeto prepara e normaliza os atributos, estabelece um classificador SVM (`SVC`) como referência e compara sua avaliação com estratégias que incorporam dados não rotulados:

- **Pseudo-labeling:** usa previsões do modelo para atribuir rótulos provisórios a novos exemplos.
- **Self-training:** itera a inclusão de exemplos rotulados pelo próprio modelo.
- **Label propagation:** propaga rótulos entre exemplos considerados semelhantes.

O desempenho é avaliado em dados de teste com o relatório de classificação do scikit-learn, incluindo acurácia, precisão, recall e F1-score. A atividade resolvida também demonstra o salvamento do modelo e do normalizador com `pickle`.

## Resultados de exemplo

A tabela resume a acurácia apresentada nos relatórios salvos nos notebooks. Cada conjunto usa sua própria divisão de treino e teste.

| Conjunto de dados | Modelo | Acurácia | Amostras no teste |
| --- | --- | ---: | ---: |
| Qualidade do leite | SVC supervisionado | 75% | 106 |
| Qualidade do leite | SVM com pseudo-labeling | 73% | 106 |
| Qualidade do leite | SVM com self-training | 85% | 106 |
| Qualidade do leite | Label Propagation | 93% | 106 |
| Diabetes | SVC supervisionado | 85% | 67 |
| Diabetes | SVM com pseudo-labeling | 87% | 67 |
| Diabetes | SVM com self-training | 87% | 67 |
| Diabetes | Label Propagation | 84% | 67 |

Esses valores são exemplos das execuções registradas nos notebooks, não uma garantia de desempenho em outros dados. Eles podem variar conforme a amostra, a divisão dos dados e os parâmetros utilizados.

## Demonstração de previsão

No teste final da aula, uma nova amostra é normalizada com `MinMaxScaler` e classificada por `LabelPropagation`. O resultado é apresentado junto às características usadas pelo modelo:

| Característica | Valor |
| --- | ---: |
| pH | 6.4 |
| Temperatura | 52 |
| Sabor | 0 |
| Odor | 1 |
| Gordura | 1 |
| Turbidez | 0 |
| Cor | 253 |
| **Qualidade estimada** | **Alta** |

Essa é uma previsão demonstrativa: como a amostra não tem uma classe real informada para comparação, o resultado não representa uma confirmação de acerto.

## Dados

- `Dados/qualidade_leite.csv`: características de amostras de leite e categorias de qualidade.
- `Dados/dados_diabetes.csv`: dados usados na atividade de classificação.

Os notebooks carregam as bases a partir do repositório público, facilitando a abertura pelo Google Colab.

## Estrutura do repositório

```text
.
├── Aulas/
│   └── Aula+5+-+Aprendizado+semi-supervisionado.ipynb
├── Atividades/
│   ├── Mão na massa.ipynb
│   └── Mão na massa (com solução).ipynb
├── Dados/
│   ├── dados_diabetes.csv
│   └── qualidade_leite.csv
├── requirements.txt
└── README.md
```

## Tecnologias e competências

**Tecnologias:** Python, pandas, scikit-learn, Matplotlib e Jupyter.

**Competências:** classificação, aprendizado semi-supervisionado, preparação e normalização de dados, comparação de modelos e avaliação com métricas de classificação.