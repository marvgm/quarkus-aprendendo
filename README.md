# quarkus-getting-started project

This project uses Quarkus, the Supersonic Subatomic Java Framework.

If you want to learn more about Quarkus, please visit its website: https://quarkus.io/ .

### Vídeo do Youtube (Todos os créditos ao autor)

https://youtu.be/pBc0qSLaHO8

# Primeira Aplicação

## Pré-requisitos
* JDK 1.8+ com JAVA_HOME configurado
* Uma IDE (Eclipse ou IntelliJ)
* Apache Maven 3.5.3+
* Docker (caso queira criar e executar uma imagem da aplicação)
* GraalVM (caso queira gerar o executável nativo para Linux)

## Passos
como instalei o Docker no linux: sudo snap install docker
olhar arquivo docker-compose.yml na pasta docker do projeto
rodar o comando: sudo docker-compose up -d
para listar containers: sudo docker ps

https://medium.com/@renato.groffe/postgresql-pgadmin-4-docker-compose-montando-rapidamente-um-ambiente-para-uso-55a2ab230b89

O projeto irá conter:

1. Estrutura maven
2. O recurso com.casa.marcos.hello.HelloResource disponível no contexto /hello e /hello/quarkus
3. Um teste de unidade para HelloResource utilizando REST Assured 
4. Uma página inicial index.html
5. Arquivos Dockerfile para criação de imagens em modo nativo e JVM
6. Arquivo application.properties para configuração das extensões

### 2. Subir aplicação com Hot Reloading e dev mode
* ./mvnw compile quarkus:dev

### 3. Acessar aplicação
* http://localhost:8080
* http://localhost:8080/hello
* http://localhost:8080/hello/quarkus

# Segundo vídeo: Utilizando Hibernate ORM

## Pré-requisitos
* JDK 1.8+ com JAVA_HOME configurado
* Uma IDE (Eclipse ou vscode)
* Apache Maven 3.5.3+
* Postgres

O projeto irá conter:

1. Estrutura maven
2. O recurso novo com.github.viniciusfcf.hibernate.ProdutoResource disponível no contexto /produtos (GET e POST)
3. A entidade com.github.viniciusfcf.hibernate.Produto
4. Arquivo application.properties foi atualizado com as configuraçãoes de banco de dados

### 2. Subir aplicação com Hot Reloading
* ./mvnw compile quarkus:dev -Dquarkus.profile=dev

### 3. Acessar aplicação
* http://localhost:8080/produtos (GET e POST)


### 2. Vídeo do Youtube

https://youtu.be/geXSv1RMvK4

# Terceiro Vídeo: Rastreando seus microsserviços com Jaeger
## Pré-requisitos
* JDK 1.8+ com JAVA_HOME configurado
* Uma IDE (Eclipse ou IntelliJ)
* Apache Maven 3.5.3+
* Docker (caso queira criar e executar uma imagem da aplicação)
* GraalVM (caso queira gerar o executável nativo para Linux)
* Postgres
  * docker pull postgres
  * docker run --network host -e POSTGRES_PASSWORD=postgres -d postgres
* Jaeger
  * docker pull jaegertracing/all-in-one
  * docker run --network host jaegertracing/all-in-one

### 2. Subir aplicação com Hot Reloading
* ./mvnw compile quarkus:dev

ver Jaeger em: http://localhost:16686/search

### 3. Vídeo do Youtube

https://www.youtube.com/watch?v=_tHkrmheW7k

## Packaging and running the application

The application is packageable using `./mvnw package`.
It produces the executable `quarkus-getting-started-1.0.0-SNAPSHOT-runner.jar` file in `/target` directory.
Be aware that it’s not an _über-jar_ as the dependencies are copied into the `target/lib` directory.

The application is now runnable using `java -jar target/quarkus-getting-started-1.0.0-SNAPSHOT-runner.jar`.

## Creating a native executable

You can create a native executable using: `./mvnw package -Pnative`.

Or you can use Docker to build the native executable using: `./mvnw package -Pnative -Dquarkus.native.container-build=true`.

You can then execute your binary: `./target/quarkus-getting-started-1.0.0-SNAPSHOT-runner`

If you want to learn more about building native executables, please consult https://quarkus.io/guides/building-native-image-guide .