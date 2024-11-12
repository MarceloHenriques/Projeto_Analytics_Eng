![Databricks](https://img.shields.io/badge/databricks-222832?style=for-the-badge&logo=databricks)
![NumPy](https://img.shields.io/badge/numpy-%23013243.svg?style=for-the-badge&logo=numpy&logoColor=white)
![Pandas](https://img.shields.io/badge/pandas-%23150458.svg?style=for-the-badge&logo=pandas&logoColor=white)
![Python](https://img.shields.io/badge/python-3670A0?style=for-the-badge&logo=python&logoColor=ffdd54)
![Apache Spark](https://img.shields.io/badge/Apache%20Spark-FDEE21?style=for-the-badge&logo=apachespark&logoColor=black)
![Apache Kafka](https://img.shields.io/badge/Apache%20Kafka-000?style=for-the-badge&logo=apachekafka)
![Jupyter Notebook](https://img.shields.io/badge/jupyter-white?style=for-the-badge&logo=jupyter&logoColor=orange)
![Visual Studio Code](https://img.shields.io/badge/Visual%20Studio%20Code-0078d7.svg?style=for-the-badge&logo=visual-studio-code&logoColor=white)
![GitHub](https://img.shields.io/badge/github-%23121011.svg?style=for-the-badge&logo=github&logoColor=white)

# Enunciado Projeto Proposto

## Projeto: Engenharia de Dados e Garantia de Qualidade no Conjunto de Dados do Airbnb no Rio de Janeiro
Introdução à Base de Dados do Airbnb
O conjunto de dados "Inside Airbnb", disponível no website "http://insideairbnb.com/", é uma valiosa fonte de informações sobre listagens de hospedagem, avaliações de hóspedes e disponibilidade de calendário em várias cidades ao redor do mundo, incluindo o Rio de Janeiro. Antes de prosseguirmos com a engenharia de dados, é importante entender os principais componentes deste conjunto de dados:

Listing (Listagem): Este conjunto de dados contém informações detalhadas sobre as propriedades listadas no Airbnb. Cada registro representa uma listagem individual e inclui informações como o tipo de propriedade, preço, localização, número de quartos, comodidades oferecidas e muito mais.

Reviews (Avaliações): O conjunto de dados de avaliações contém informações sobre as avaliações feitas por hóspedes que ficaram nas propriedades listadas. Ele inclui dados como a data da avaliação, o identificador da propriedade, os comentários escritos pelos hóspedes, e outras informações.

Calendar (Calendário): Este conjunto de dados contém informações sobre a disponibilidade das propriedades ao longo do tempo. Ele lista as datas em que as propriedades estão disponíveis para reserva, bem como os preços para cada data.

O dicionário dos dados também está disponível no website: "http://insideairbnb.com/".

## Passos do Projeto
Aquisição de Dados e Armazenamento de Dados em PostgreSQL - Camada Bronze
Baixe o conjunto de dados "Inside Airbnb" do Rio de Janeiro da fonte oficial (http://insideairbnb.com/) e promova uma estruturação simples nos dados.
Crie um banco de dados PostgreSQL para armazenar os dados brutos das 3 tabelas ("Listing", "Reviews" e Calendar") na camada "bronze".

### Data Clean - Camada Silver:
Identifique e lide com valores ausentes, duplicatas e outliers nos dados brutos da camada "bronze".
Padronize e limpe os nomes das colunas, convertendo-os em um formato consistente.
Realize uma limpeza textual em campos, como descrições de propriedades, removendo caracteres especiais e erros de digitação.

### Data Quality - Camada Silver:
Defina métricas de qualidade de dados, como integridade, precisão e consistência para os dados da camada "bronze".
Implemente verificações para garantir que os dados da camada "silver" estejam em conformidade com essas métricas.
Estabeleça um sistema de monitoramento contínuo da qualidade dos dados da camada "silver".

### Testes de Qualidade - Camada Silver:
Utilize a biblioteca Great Expectations para criar testes de qualidade automatizados que verifiquem as expectativas definidas para os dados da camada "silver".
Desenvolva testes que assegurem que os dados da camada "silver" atendam às regras de negócios e aos requisitos de qualidade.

### Transformação de Dados com dbt - Camada Silver:
Utilize a ferramenta dbt para criar a camada "silver" de dados, realizando transformações e preparando os dados da camada em questão.
Mantenha um controle de versão dos modelos dbt relacionados à camada "silver" e automatize a execução das transformações.
 
### Armazenamento de Dados em PostgreSQL - Camada Silver:
Armazene os dados da camada "silver" no mesmo banco de dados PostgreSQL.
Estabeleça conexões entre o dbt e o PostgreSQL para carregar os dados transformados da camada "silver" no banco.

### Validação de Expectativas com Great Expectations - Camada Silver:
Implemente validações adicionais usando Great Expectations nas camadas de dados da camada "silver".
Monitore a qualidade dos dados da camada "silver" após cada transformação e ajuste os testes de acordo.

### Transformação de Dados com dbt - Camada Gold:
Utilize o dbt para criar a camada "gold" de dados, aplicando agregações especializadas, como médias de preços por propriedade, por período, e outras agregações especializadas.
Mantenha um controle de versão dos modelos dbt relacionados à camada "gold" e automatize a execução das transformações.
Armazene os dados da camada "gold" no mesmo banco de dados PostgreSQL, mantendo a estrutura de dados otimizada para consultas analíticas.


# Projeto

O projeto tem como objetivo ser utilizado no Databricks. Dessa forma os notebooks são efetivamente o projeto e aplicação. Os arquivos CSV originais utilizados neste projeto são de tamanho considerável, o que inviabiliza sua inclusão direta no repositório GitHub. Para replicar o projeto localmente, você pode baixar os dados necessários através do site Inside Airbnb (https://insideairbnb.com/get-the-data/), que fornece acesso a arquivos atualizados com informações detalhadas sobre listagens de aluguéis temporários.


# Databricks

A seguir estão os detalhes de cada notebook que deve ser importado para o ambiente Databricks. O arquivo DBC consolidado contém todos os notebooks necessários, permitindo a importação completa de uma única vez. Alternativamente, caso prefira, é possível realizar a importação de cada notebook individualmente para análise separada.

### bronze.ipynb

Nessa etapa foi realizado o upload dos arquivos listing.csv, calendar.csv e reviews.csv para o ambiente Databricks, onde cada arquivo foi carregado e transformado em DataFrames para facilitar a análise dos dados. Foram aplicados ajustes para otimizar a visualização e a consistência dos DataFrames, garantindo que as colunas estivessem corretamente formatadas e prontas para processamento. Após essas preparações, cada DataFrame foi salvo no formato Delta, possibilitando um armazenamento eficiente e adequado para consultas rápidas e persistentes ao longo do projeto.

### listing_silver.ipynb / calendar_silver.ipynb / reviews_silver.ipynb

Nessa etapa, foram aplicados diversos tratamentos ao DataFrame para garantir a integridade e a conformidade dos dados. As ações incluíram a remoção de linhas duplicadas, a padronização de tipos de dados (tipagem) conforme necessário e a verificação detalhada de colunas com valores nulos, assegurando que os dados estivessem completos e prontos para análise. Após o tratamento, utilizamos o framework Great Expectations para validar a qualidade e conformidade dos dados, definindo expectativas específicas que asseguraram a aderência dos valores aos padrões requeridos. Esse processo fortaleceu a consistência e confiabilidade dos dados antes das próximas fases do projeto.

### gold.ipynb

Na camada Gold, foi realizada a consolidação dos dados para uma análise mais detalhada e avançada dos principais indicadores. Inicialmente, verificamos o número de registros nas tabelas listing_silver e calendar_silver, além de assegurar a correspondência entre os IDs dessas tabelas. Em seguida, calculamos o total de registros por anúncio para confirmar a disponibilidade de entradas no calendário para cada um. Também foram extraídas métricas como taxa de ocupação, preço médio por noite e média de avaliações, tanto por ID de anúncio quanto por bairro, permitindo insights aprofundados sobre a ocupação e o comportamento de preços em diferentes regiões e localidades.


# Conclusão  
Este projeto foi estruturado para realizar uma análise profunda e abrangente dos dados de aluguel temporário, utilizando o Databricks como ambiente de processamento e armazenamento. Na camada Bronze, os dados originais em CSV foram carregados, transformados em DataFrames e salvos no formato Delta, criando uma base inicial robusta e eficiente para a exploração dos dados. Na camada Silver, os dados passaram por uma série de transformações e verificações que incluíram a eliminação de duplicidades, ajustes de tipagem e análise de valores nulos. Utilizamos o Great Expectations para validar a qualidade dos dados, assegurando que cada coluna estivesse conforme os padrões definidos, o que reforça a integridade dos dados e sua adequação para a análise.

Na camada Gold, consolidamos os dados e extraímos indicadores essenciais, como taxa de ocupação, preço médio por noite e média de avaliações, tanto por anúncio quanto por bairro. Essa camada permitiu a criação de uma visão geral detalhada sobre os padrões de ocupação e o comportamento de preços, permitindo insights mais profundos sobre a distribuição e a qualidade das acomodações oferecidas em diferentes regiões. Esse pipeline estruturado em três camadas proporcionou um fluxo de dados eficiente e consistente, possibilitando análises confiáveis e enriquecidas para a compreensão do mercado de aluguel temporário.




