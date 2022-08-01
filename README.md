# Machine Learning Classifier

## Como executar os códigos? 🧑‍💻
Crie um ambiente virtual Python:
```bash
python3 -m venv /path/to/new/virtual/environment
```

Ative o ambiente virtual: 
```bash
source /path/to/new/virtual/environment/bin/activate
```

Instale as dependências com ``deploy/requeriments.txt``:
```bash
pip install requeriments.txt
```

Adicione o ambiente virtual ao "kerneis" do Jupyter Notebook (Jupyter Lab):
```bash
python3 -m ipykernel install --name environment
```

Executada a última instrução o ambiente virtual deverá aparecer na lista de "kerneis" do Jupyter Notebook (Jupyter Lab), selecione-o e divirta-se! 😄
## Introdução
Dentre os algoritmos testados para a resolução do problema a *Regressão Logística* apresentou o melhor resultado. Além deste foram testados os algoritmos *Árvore de Decição*, *K Nearest Neighbors (KNN)* e *Support Vector Machine (SVM)*. Devido a baixa quantidade de dados *Redes Neurais* foram desconsideradas.

Para uma melhor acompanhamento das etapas desse projeto sugiro a seguinte *timeline* de leitura e/ou execução dos arquivos:
1. ``data_cleaning.ipynb``
2. ``eda.html``
3. ``logistic_regression.ipynb``
4. Diretório ``deploy``

## Análise Exploratória dos Dados (AED) 📊
Foi realizanda uma AED automática usando o pacote DataPrep. Ela fornece uma excelente visão geral dos dados. Uma AED mais específica é feita na etapa de preparação dos dados de cada algoritmo. Para visualizar a AED automática abra no seu navegador o arquivo ``eda.html``.

## Preparação dos Dados
Em geral, diferentes algoritmos possuem diferentes premissas, normalmente, implicando em diferentes métodos de preparação de dados para diferentes algoritmos. Neste problema foi usado o algoritmo Regressão Logística, que possue as seguintes particularidades na preparação dos dados:

**Vairável de Saída Binária**: A regressão logística é pensada para a classificação binária

**Remover o Ruído**: A regressão lógistica assume erro zero na variável de saída (target), considere remover outliers e poissíveis amostras classificadas errôneamente do conjunto de treinamento.

**Distribuição Gaussiana**: A regressão lógistica é um algoritmo linear (com uma transformação não linear na saída). Ele assume uma relação linear entre as variáveis de entrada com a variável de saída. Transformar as variáveis de entrada de modo a expor melhor essa relação pode lever a um modelo mais acurado. Por exemplo, use log, raiz, Box-Cox e outras transformações univariadas para explor melhor essa relação.

**Remover Entradas Correlacionadas**: Assimo como na Regressão Linear, o modelo pode overfit se existirem muitas variáveis de entradas altamente correlacionadas. Considere calcular a correlação entre as variáveis de entrada e remover entradas altamente correlacionadas.

**Falhar ao Convergir**: É possível no processo de aprendizagem a falha ao convergir nos valores do coeficientes. Isto pode acontecer se existirem muitas entradas correlacionadas ou se os dados são muito esparsos (por exemplo, muitos zeros nas variáveis de entrada).

Mais detalhes podem ser verificados no Jupyter Notebook ``logistic_regression.ipynb``.

## Avaliação de Performance
Se tratando de um problema de classificção com natureza dos dados desconhecidas achei rasoável usar usar a métrica *acurácia* para avaliar a performance do modelo. O conjunto de teste consiste em uma amostra estratificada de 20% dos dados do conjunto original.

## Deploy do Modelo
O modelo foi colocado em produção através de uma API contruída com o *framework* Flask disponibilizada na plataforma Heroku. O *endpoint* para obter as previsões do modelo é: (https://machine-learning-classifier.herokuapp.com/predict)

Para acessar os códigos da API veja: (https://github.com/hagijakobson/machine-learning-classifier-api)

No Jupyter Notebook ``logistic_regression.ipynb`` vê-se um exemplo de como usar a API. 
