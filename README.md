## 👋 Olá, eu sou a Jefferson Reis! 
Este desafio consiste em extrair os dados de um arquivo .csv, através da Api Rest (GET) do GitHub e utilização do Pandas (Python).

Realizar o processo de captura destes dados e na sequência arquivá-los em outro arquivo .csv com TODOS os dados retornados da API REST (GET) do GitHub, utilizando API REST (PUT)

## 💡 Tecnologias e extensões Utilizadas 

 - [Api GitHub](https://api.github.com/)
 - [Visual Studio Code](https://code.visualstudio.com/)
 - [Code Runner](https://www.google.com/url?sa=t&rct=j&q=&esrc=s&source=web&cd=&cad=rja&uact=8&ved=2ahUKEwjVhdnE5OGBAxW9uJUCHSSqBXwQFnoECBgQAQ&url=https%3A%2F%2Fmarketplace.visualstudio.com%2Fitems%3FitemName%3Dformulahendry.code-runner&usg=AOvVaw0r_NmkPwigsaityd4Ng23-&opi=89978449)

## 📌 Uso/Exemplos

```python
## Leitura de dados de um arquivo .csv ##

import pandas as pd
df = pd.read_csv('NOME_DO_SEU_ARQUIVO.csv')
users_names = df['NOME_DA_COLUNA_REFERENCIA'].tolist()
print(users_names)
```
```python
## Obter dados de cada username pela api do Github (https://api.github.com/) ##

import requests
import json

print('GitHub Users\n')

url_api_github = 'https://api.github.com/users/'

def get_user(username):
    response = requests.get(f'{url_api_github}{username}')
    return response.json() if response.status_code == 200 else None

# Use os nomes de usuário do CSV na compreensão de lista
logins = [get_user(username) for username in users_names if (user := get_user(username)) is not None]
print(json.dumps(logins, indent=2))
```

```python
## Salvando os dados recuperados dentro do arquivo .csv ##

# Criação de  um DataFrame a partir dos dados
user_data_df = pd.DataFrame(logins)

# Salve o DataFrame em um arquivo CSV
user_data_df.to_csv('dados_usuarios_github.csv', index=False)
```

## 💡 Screenshots 

<div align="center">
 <img src="https://github.com/jeffersonreislima/desafio_etl_python/assets/142839931/f07a1266-0267-4d44-a1fd-3dec4e009789" />
</div>
