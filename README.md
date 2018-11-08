# Este repositório contém os seguintes recursos do Docker:

    Dockerfiles para criar imagens docker
    Docker composer e arquivos para avaliar a implementação simples do WSO2 EI com o banco de dados MySQL.

- O Dockerfiles nos permite construir imagens do Docker genéricas para implantar o produto em ambientes contêineres.
 - O Dockerfile base inclui o JDK e a distribuição do produto.
Configurações, driver JDBC, extensões e outros artefatos implementáveis ​​são projetados para serem fornecidos por meio de montagens de volume.

O arquivo Docker Compose faz uso das imagens docker do WSO2 Enterprise Integrator e MySQL.
