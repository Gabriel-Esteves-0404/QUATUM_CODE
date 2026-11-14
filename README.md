# Classificador Quântico de Raios-X (COVID vs. Normal)

[![Abrir no Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/Gabriel-Esteves-0404/QUATUM_CODE/blob/main/BASECOD.ipynb)

Experimento de **aprendizado de máquina quântico** que classifica imagens de raio-X de tórax em duas classes (**Normal** e **COVID**) usando um circuito quântico variacional de 4 qubits, simulado com [PennyLane](https://pennylane.ai/).

> Projeto de estudo, com foco em aprender computação quântica aplicada a dados reais. Os resultados são preliminares.

## Como funciona

1. **Pré-processamento:** imagens convertidas para escala de cinza e redimensionadas para 64×64 pixels.
2. **Redução de dimensão:** PCA para 4 componentes (uma por qubit), seguido de padronização.
3. **Codificação:** as 4 features entram no circuito por portas `RX` e `RY`.
4. **Circuito variacional:** 5 camadas de rotações parametrizadas e emaranhamento, com medição de um observável para gerar a predição.
5. **Treinamento:** otimizador Adam (passo 0,001), função de perda *Binary Cross Entropy*, 600 passos com mini-lotes de 10 amostras.
6. **Avaliação:** divisão de 80% treino e 20% validação.

Para manter a simulação rápida, o experimento usa um subconjunto de 50 imagens por classe.

## Resultados

Na execução registrada no notebook, a acurácia de validação ficou em torno de **55–60%**. O modelo ainda não é competitivo com classificadores clássicos, e o objetivo aqui é entender a técnica. Ideias para melhorar: mais componentes/qubits, outros *ansätze*, mais dados e ajuste de hiperparâmetros.

## Estrutura

```
├── BASECOD.ipynb          # Notebook principal
├── BASECOD_backup.ipynb   # Cópia anterior do notebook
├── DATASET/               # Imagens e máscaras (COVID e Normal, 200 de cada)
└── PARAMS_SALVOS/         # Parâmetros treinados do circuito (.npy)
```

## Como executar

**No Colab:** clique no botão acima e execute as células em ordem. O notebook instala o PennyLane e clona este repositório para acessar o `DATASET`.

**Localmente:**

```bash
pip install pennylane pennylane-lightning scikit-learn matplotlib pillow numpy
jupyter notebook BASECOD.ipynb
```

(Ajuste o caminho do dataset na célula de importação, caso não use o Colab.)

## Tecnologias

Python · PennyLane · NumPy · scikit-learn · Matplotlib · Pillow

## Autor

Gabriel Esteves — [GitHub](https://github.com/Gabriel-Esteves-0404)
