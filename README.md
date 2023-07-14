# Credit Card Transactions - Carga de Dados ETL

O armazenamento de dados em um SGBD é uma etapa essencial para o uso no contexto de uma empresa. Um dado quando armazenado, também deve estar disponível para acesso das áreas e times interessados. Pensando no contexto mais tradicional, para que um dado seja aplicado em análises, é necessário que ele seja coletado e armazenado.

Dependendo de como os dados estão organizados, uma alternativa para esse armazenamento é o uso de um banco de dados relacional. Durante preparação dos dados e a insersação no banco, deve-se levar em consideração o relacionamento entre tabelas e a redudância de dados, pois existe um custo atrelado ao armazenamento e consulta. Esse é um trabalho essêncial nas etapas de engenharia de dados, mais especificamente armazenamento e dispobilidade de dados.


## Objetivo

O escopo aqui delmitado é a criação de um banco de dados e carga de dados em um processo ETL, utilizando apenas ferramentas básicas de manipulação de dados e o connector do SGBD em questão. Deverá ser considerado o custo de armazenamento e consultas. Além disso, serão realizadas otimizações na formo como os dados serão armazenados, incluindo informações de metadados, que em um ambiente real possuem valor na organização dos dados e auxilio na realização de consultas de áreas interessadas.

## Pré-requisitos

Para realização dessa atividade serão utilizadas as seguintes ferramentas e pacotes:

* Download dos Arquivos Utilizados
* Banco de dados MariaDB;
* Python 3 e Pacotes.

### Download dos Arquivos Utilizados

Todos arquivos de dados utilizados podem ser baixados no site [Kaggle](https://www.kaggle.com/datasets/ealtman2019/credit-card-transactions/discussion/277100). É necessário uma conta no site para realizar o Download dos arquivos. O único pré-requisito é manter o arquivo arquivo na mesma pasta em que o arquivo jupyter-notebook está.

É possível encontrar mais informações sobre os arquivos e as licença nos tópicos [Descrição dos Arquivos](#descrição) e [Licença](#licença).

### Instalação do MariaDB
 
A forma mais rápida e prática de se contruir um banco de dados MariaDB é criando um container. O exemplo apresentado utilizará a sintaxe docker, que também pode ser utilizada com o podman, apenas alterando a palavra docker para podman.

Substitua `my-secret-pw` pela senha desejada.

docker run --name mariadb -p 3406:3306 -e MARIADB_ROOT_PASSWORD=my-secret-pw -d mariadb:latest

### Instalação do Python 3 e Pacotes

Não será tratada aqui a instalação do Python 3. No entanto, a versão em questão que foi utilizada no projeto é a versão 3.11.1. As versões dos pacotes utilizados foram:

* mariadb: 1.1.7
* pandas : 2.0.3
* numpy  : 1.24.4

Para instalar os pacotes basta utilizar o comando `pip3 install nome_pacote`. 

Para o pacote mariadb pode ser necessário que se possua instalado o `libmariadb-dev` ou `mariadb-connector-c`. No linux Debian e derivados, esses pacotes podem ser facilmente instalados utilizando o comando `sudo apt install -y nome_pacote`.


## Descrição dos Arquivos <a name="descrição"></a>

Os dados que serão utilizados para carga ETL podem ser acessados [clicando aqui](https://www.kaggle.com/datasets/ealtman2019/credit-card-transactions/discussion/277100), e foram gerados a partir de uma simulação realizada pela IBM de transações de cartões. A vantagem do uso desses dados para o objetivo especificado é a possibilidade de diminuição de criação de tabelas intermediárias, para otimizar o espaço de armazenamento. Além há a necessidade de tratamento básico em algumas variáveis, que é justamente um trabalho necessário no processo de ETL para disponibilização do dado para consumo.Descrição dos Arquivos

Os arquivos são uma simulação de transações de cartão de crédito e possuem mais de 24 milhões de linhas de dados sintéticos. Ao todo há disponível 4 arquivos csv, porém, serão utilizados apenas 3 arquivos, pois um deles é a geração de dados de apenas 1 usuário.

Os dados gerados tratam de informações especificas de usuários, cartões e das transações propriamente ditas.


## Licença

Os dados utilizados para construção do projeto foram reditados dos [Kaggle](https://www.kaggle.com/datasets/ealtman2019/credit-card-transactions/discussion/277100), publicados por Erik Altman, Apoorva Nitsure IBM e Youssef Mroueh.

Os dados estão disponibilizados sob a licensa Apache 2.0, e o arquivo LICENSE pode acessado [clicando aqui](./LICENSE), conforme descrito pelos termos da licença.
