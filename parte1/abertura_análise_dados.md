# Introdução
Finalmente vamos iniciar o nosso projeto! Aqui iremos fazer a importação das nossas bibliotecas, vamos abrir o dataset e fazer uma análise básica sobre do que se trata a base. 

```python
import pandas as pd
import numpy as np
import seaborn as sns
import matplotlib.pyplot as plt
import plotly.express as px
``` 
Sempre que importamos uma biblioteca, passamos um apelido para ela, para que fique mais fácil nossa utilização, e é isso que o *as* pd, *as* np, e os demais significam. 

## Leitura da Base
Após importado as bibliotecas, vamos finalmente abrir nossa base pela primeira vez. Para isso, utilizaremos a biblioteca *pandas* e seu método *read_csv*.

```python
base_credit = pd.read_csv('credit_data.csv')
``` 
Adicionamos esse método em uma variável, e passamos o *path* do arquivo como parâmetro. 
Agora vamos fazer nossa primeira visualização, para isso, utilizaremos o comando .head() do próprio pandas. Ele nos retornará as 5 primeiras linhas do arquivo. 
```python
base_credit.head()
``` 
Saída: 

![image](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/3j3iu97tnehvxxg3gqww.png)

Podemos ver que temos uma tabela, com 6 colunas. 
1. A primeira coluna corresponde ao índice da nossa tabela, qual o tamanho dela; 
2. A segunda coluna (clientid) corresponde ao id do cliente; 
3. A terceira coluna (income) corresponde ao salário do respectivo cliente ao ano. 
4. A quarta coluna (age), mostra a idade do cliente; 
5. A quinta coluna (loan), representa o valor da dívida que o cliente está devendo; 
6. E por ultimo, a sexta coluna, representa se o cliente quitou, ou não, a dívida. Esses valores são representados por 1 e 0, respectivamente.  

## Exploração dos dados - início
Para fazer a exploração, utilizaremos o comando describe, do pandas. Ele retornará diversas informações estatísticas dos valores números existentes na nossa tabela. 

```python
base_credit.describe()
``` 
Saída: 

![image](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/k3x9ffwmlz7215gq7fja.png)

Com esse comando podemos observar a quantidade de linhas contidas na tabela, a média de cada uma das colunas, o desvio padrão, o valor mínimo encontrado, o primeiro quartil de 25%, a mediana, o segundo quartil de 75% e o valor máximo encontrado. 

Agora vamos observar quais valores possíveis temos na váriavel default, a que representa se o cliente pagou ou não a dívida. Para isso, vamos utilizar a biblioteca numpy, passando o comando *unique*
```python
np.unique(base_credit['default'])
``` 
Saída: 

```python
array([0, 1])
``` 
Vamos passar o mesmo comando agora, porém com o parâmetro *return_counts*, para sabermos qual a quantidade de valores de 0 e 1 temos na base
```python
np.unique(base_credit['default'], return_counts=True)
``` 
Saída:

```python
(array([0, 1]), array([1717,  283]))
```

Agora, utilizaremos a biblioteca seaborn e o próprio pandas para gerar alguns gráficos que facilite nossa exploração de dados 

```python
sns.countplot(x=base_credit['default']);
plt.hist(x=base_credit['age']);
plt.hist(x=base_credit['income']);
plt.hist(x=base_credit['loan']);
``` 
Saída: 

![image](https://user-images.githubusercontent.com/56757180/122453414-ba1a9580-cf80-11eb-80ff-424e4ebd22ab.png)

![image](https://user-images.githubusercontent.com/56757180/122453488-cacb0b80-cf80-11eb-96c2-20f257e48239.png)

![image](https://user-images.githubusercontent.com/56757180/122453514-d4ed0a00-cf80-11eb-846d-024cb7ace984.png)

![image](https://user-images.githubusercontent.com/56757180/122453603-f0581500-cf80-11eb-98cf-06ad977c195b.png)

# Link para o notebook
Para acessar o código como um todo, basta clickar [aqui](https://colab.research.google.com/github/DevShy/MachineLearningProject/blob/main/explorativeDataset.ipynb#scrollTo=T2wvs_WgLQ3q)  
