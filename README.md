# AGILE MANAGMENT - EVERTON VASZELEWSKI
# MVP SPRINT 4 - Pós-Graduação em Engenharia de Software

---
## Contém

- MVP Canvas e Lean Inception completo no Miro. Para acessar, abra este [LINK](https://miro.com/app/board/uXjVKcTozKY=/?share_link_id=775719527704).
- Arquivo PDF contendo a descrição do Cenário Hipotético, Contexto, Stakeholders e Equipe do Projeto.
- Página Kaggle do dataset Graduate Admission como referência e fonte: [Kaggle](https://www.kaggle.com/datasets/mohansacharya/graduate-admissions/data)
- Video de Apresentação e Execução do Projeto no [YouTube](https://www.youtube.com/watch?v=t-cheeZpgYo)
- Pasta "Original CSV Files" com o dataset original da fonte e dataset tratado (Chance Of Admit)
- Arquivos referente a aplicação Full-stack para fazer a carga do arquivo do modelo de machine learning no back-end e possibilitar a entrada de novos dados no front-end para que o modelo de classificação faça a predição da classe de saída e exibir o resultado na tela.

---
## Descrição e Contexto
Este projeto tem como intenção calcular a predição das chances de uma pessoa ingressar no Ensino Superior nos Estados Unidos através da perspectiva de um indiano (critério especificado na descrição do dataset).
O dataset utilizado possui sete parâmetros que são relevantes e importantes durante a inscrição para programas de Mestrado, por exemplo.
Segue abaixo os parâmetros:

- GRE Scores ( entre 0 e 340 )
- TOEFL Scores ( entre 0 e 120 )
- University Rating ( entre 0 e 5 )
- Statement of Purpose ( entre 0 e 5 )
- Letter of Recommendation Strength ( entre 0 e 5 )
- Undergraduate GPA ( entre 0 e 10 )
- Research Experience ( valor 0 ou 1 )
- Chance of Admit ( valor 0 ou 1 )

Os valores referentes ao campo "Chance of Admit" foram tratados e convertidos. No dataset original, os valores iam de 0.0 até 1.0, e como estamos fazendo uma classificação, não eram valores válidos. Portanto, os valores que iam de 0.0 até 0.69 receberam o valor 0 (Não aprova para processo) e valores que iam de 0.70 até 1.0 receberam o valor 1 (Aprovados no processo).

Em relação as boas práticas de Desenvolvimento de Software seguro, neste caso, o dataset se apresenta de forma totalmente anônima e livre de responsabilidades para com qualquer indivíduo, o mesmo apresenta apenas dados numéricos, respeitando os intervalos dos campos, sem distinção de idade, gênero, identificações ou valor de mesma natureza, portanto podemos ver um exemplo simples e aplicável para o sistema.

---
## Como executar predict_api e predict_front

Requisitos:
- Realizar a instalação das libs python listadas no `requirements.txt`.
- É recomendado o uso de ambientes virtuais do tipo [virtualenv](https://virtualenv.pypa.io/en/latest/installation.html).


1 - Após clonar o repositório, é necessário ir ao diretório raiz, pelo terminal, para poder executar os comandos descritos abaixo:

cd pucrio-mvp-sprint3-dataset-master\predict_api

2 - Instalar Virtualenv
```
$ pip install VirtualEnv
```

3 - Criar Virtualenv
```
$ Virtualenv venv
```

4 - Ativar venv
```
$ venv\scripts\activate
```

5 - Instalar libs python
```
(venv)$ pip install -r requirements.txt
```

6 - Executar API:
```
(venv)$ flask run --host 0.0.0.0 --port 5000
```

Em caso de modificações no código enquanto a API estiver rodando, utilizar o parâmetro reload, que reiniciará o servidor
automaticamente após uma mudança no código fonte. 

```
(env)$ flask run --host 0.0.0.0 --port 5000 --reload
```

Após seguir todos os passos, abrir o link abaixo no bavegador para verificar o status da API em execução
- [http://localhost:5000/#/](http://localhost:5000/#/)

Link para Documentação:
- [http://127.0.0.1:5000/openapi/]

Para utilização da interface Front-End, execute o arquivo "index.html" em um navegador de sua preferência

---
## Critério e execução da classe de Teste

Para a Classe de Teste, o critério para validação é a Acurácia do modelo KNN. Para aprovação, foi definido que o resultado seja maior que 0.6 (60%) de acurácia.

Foi utilizado 200 dados aleatórios dos 400 dados do dataset tratado. Foram utilizados os mesmos dados pelo fato de o dataset não possuir tantos registros para divisão entre treino e teste.

Instruções para execução:

1 - Após clonar o repositório, é necessário ir ao diretório raiz, pelo terminal, para poder executar os comandos descritos abaixo:

cd pucrio-mvp-sprint3-dataset-master\predict_api

2 - Executar o comando abaixo para obter o resultado do Teste com a metodologia de classificação KNN
```
$ pytest –v test_modelos
```

