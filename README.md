# myfinance-web-dotnet
Sistema Financeiro Web Pessoal

## Orientações:
Comandos dotnet build e dotnet run precisam ser executados dentro da pasta onde se encontra os arquivos da aplicação.
Navegar com cd para poder se localizar na pasta correta

### Dotnet build
Compila o arquivo myfinance-web-dotnet.csproj

### Dotnet run
Executa a aplicação compilada.

### Criar projetos (camadas) de serviços, dominio e infraestrutura

No terminal, na pasta raiz da aplicação, executar os comandos:

- dotnet new classlib -n "myfinance-web-dotnet-infra"
- dotnet new classlib -n "myfinance-web-dotnet-service"
- dotnet new classlib -n "myfinance-web-dotnet-domain"

### Adicionar referências entre as camadas:

No projeto 1 (aplicação) adicionar uma referência para o projeto da camada de serviços, infraestrutura e domínio.
No projeto 2 (serviços) adicionar uma referência para o projeto da camada de infraestrutura e domínio.
No projeto 4 (infra) adicionar uma referência para o projeto da camada de domínio.

# Arquitetura MVC
Os sufixos dos objetos dentro das pastas Model, View e Controller devem ser respeitados, ou seja, um arquivo dentro da pasta controller deve chamar QqCoisaControlller.

## Model
Especificações de dados.
Model não é um espelho da entidade de domínio. Podem ter classes no model para trafegar com a view que não são entidades de domínio.

## View
Recursos pelo qual o usuário irá interagir com a aplicação

- HTML - Formulários
- PDF
- Imagens

## Controler
Representam as rotas que vão renderizar as views e receber os formulários recebidos pelos usuários e fazer uma requisição para uma camada superior para persistir os dados.
Para cada controler é preciso ter uma ou mais views.

Dentro de uma IActionResult precisa ter o nome da respectiva view.
 
# Entity Framework

## ORM - Object Relational Mapping
ORM (mapeamento objeto-relacional) é uma técnica que permite criar uma camada de mapeamento entre um modelo de objetos e um modelo relacional. 
O ORM é uma ferramenta que facilita a interação entre aplicações e bancos de dados. Com o ORM, os desenvolvedores podem trabalhar com estruturas de banco de dados diretamente no código, sem precisar escrever consultas SQL manualmente. 

### Vantagens do ORM

- Permite escrever menos código do que escreveria ao usar SQL bruto
- Facilita a atualização e manutenção do projeto
- Torna o tempo de desenvolvimento mais ágil
- Permite manipular os dados de forma eficiente
- Remove as complexidades permitindo maior produtividade

### Exemplos de ORM 

- Django ORM, integrado ao framework web Django
- Eloquent ORM, usado no Laravel para lidar com bancos de dados
- Frameworks ORM como Hibernate e JPA

### Entity Framework Core

Link - https://learn.microsoft.com/pt-br/ef/core/what-is-new/ef-core-9.0/whatsnew

# Camadas da arquitetura:

## 1- myfinance-web-dotnet (Aplicação)

Adicionar na classe Program.cs a instancia da classe MyFinanceDbContext.cs como um serviço.

## 2- myfinance-web-dotnet-service (Serviços)

Criar dois arquivos C# do tipo interface, sendo um com nome IPlanoContaService.cs e outro com nome ITransacaoService.cs. Eles serão responsáveis por orquestrar as solicitações ao banco de dados.

Criar as classes de serviços para as duas interfaces e injetar nela o objeto DbContext.

## 3- myfinance-web-dotnet-domain (Domínio)

Criar uma pasta Entities e dentro dela criar as classes que de cada entidade (PlanoConta e Transacao):

## 4- myfinance-web-dotnet-infra (Infraestrutura)

É a camada responsável pelo acesso ao banco de dados.

#### Classe MyFinanceDBContext.cs

É a classe que fará o acesso aos dados (DAL).
O termpo DBContext é um conceito do Entity. É uma das classes que ele utiliza para realizar o mapeamento.

Para fazer a inclusão da biblioteca do Entity é necessário baixar atraves do site [hnuget.org/packages](https://www.nuget.org/PACKAGES).

Certifique-se de estar na camada de infra e execute o comando para instalar as bibliotecas Microsoft.EntityFrameworkCore e compativel com a versão de .NET instalada. Nesse exemplo foi utilizada a versão 9.0.2, respectivamente através dos comandos "dotnet add package Microsoft.EntityFrameworkCore --version 9.0.2" e "dotnet add package Microsoft.EntityFrameworkCore.SqlServer --version 9.0.2".

- Conection string
Acessar o site https://www.connectionstrings.com/sql-server/ para obter.