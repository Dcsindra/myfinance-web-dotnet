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

# MVC
Os sufixos dos objetos dentro das pastas Model, View e Controller devem ser respeitados, ou seja, um arquivo dentro da pasta controller deve chamar QqCoisaControlller.

## Model
Especificações de dados

## View
Recursos pelo qual o usuário irá interagir com a aplicação

- HTML - Formulários
- PDF
- Imagens

## Controler
Representam as rotas que vão renderizar as views e receber os formulários recebidos pelos usuários e fazer uma requisição para uma camada superior para persistir os dados.

