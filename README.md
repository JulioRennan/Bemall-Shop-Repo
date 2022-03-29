# Bemall-Shop-Repo

![logo bemall](https://user-images.githubusercontent.com/57741609/160401695-4c8eeaa7-0c80-4899-9cfe-dc71249e9e77.png)

##
Tabela de conteúdos
=================
<!--ts-->
   * [Pontos cumpridos do desafio](#pontos-cumpridos-do-desafio)
   * [Setup do Projeto](#setup-do-projeto)
      - [Backend](#backend)
      - [Mobile](#mobile)
   * [Telas Referente ao Desafio](#telas-referente-ao-desafio) 
   * [Descrição do Projeto](#descrição-do-projeto)
   * [C4-Model](#c4-model)
   * [Design do Backend](#design-do-backend)
   * [Design Mobile](#design-mobile)

<!--te-->

# Pontos cumpridos do desafio:
- [x] Nome ao projeto
- [x] Implementação única que permita cadastro do usuário.
- [x] Instruções de uso para execução do projeto.  
- [x] Diagrama C4
- [x] Design da solução.
- [x] Questionário respondido em .txt
##

# Setup do Projeto

O projeto foi divido em 2 componentes principais: o Backend reposável por processar toda a lógica de criação de conta/autenticação. E o Mobile é a interface que permite o usuário criar/autenticar usuários. O projeto deve funcionar independente do editor de texto usado, mas eu recomento utilizar o  [Visual Studio Code](https://code.visualstudio.com/download)

### Backend
A implementação é uma API REST simples que necessita realizar as instalações das seguintes ferramentas para funcionar:
 - [**NodeJS**](https://nodejs.org/en/download/): Ambiente de execução JavaScript server-side.
 - [**Docker**](https://docs.docker.com/engine/install/ubuntu/): será utilizado um container rodando um banco postgres para ser nossa base de dados.
 - [**TypeScript**](https://www.typescriptlang.org/download): adiciona tipagem ao JavaScript, permitindo ter um código mais organizado e legivel.
 - [**Yarn**](https://classic.yarnpkg.com/lang/en/docs/install/#mac-stable): gerenciador de pacote utilizado no projeto, porque não npm? Porque os dois funcinam de forma semelhante, no entanto o **Yarn** tem uma sintaxe mais inchuta.

Após realizar instalar todas as ferramentas execute os seguintes passos:
  - Clone o repositório do [Backend](https://github.com/JulioRennan/Bemall-Backend/tree/087ed4f482a1d5dd9809aefee3ef669fb27c6f43)
  - Dentro da pasta do repositório execute: ```yarn ```
  - Crie um container postgres: ```docker run --name bemall-postgres-db -e POSTGRES_PASSWORD=240301 -p 5432:5432 -d postgres```
  - Rode as migrations do banco de dados:  ```yarn typeorm migration:run```
  - Pronto, seu ambiente está configurado basta rodar: ```yarn dev```
  
### Mobile
A implementação da interface mobile foi feita utilizando o framework Flutter e para funcionar corretamente necessita das seguintes ferramentas:
   - [**Flutter SDK**](https://flutter.dev/docs/get-started/install).
   - [**Android Studio**](https://developer.android.com/studio): ferramenta para desenvolvimento Android Nativo.
   - [**AVD Manager**](https://developer.android.com/studio/run/managing-avds?hl=pt-br): ferramenta para configurar um novo simulador Android.

Após instalar todas as ferramentas execute os seguintes passos:
   - Clone o repositório do [App](https://github.com/JulioRennan/Bemall-App)
   - Execute: ```flutter pub get```
   - Inicie um device Android do **AVD Manager**
   - Substitua o IP na variavel ```baseUrl```, pelo seu IP interno de sua rede dentro do arquivo ```lib/constants.dart```
  
   - Execute: ```flutter run```

**_*Lembre-se que o backend deve estar rodando_**

##
# Telas Referente ao Desafio
![Telas Referente ao Desafio](https://user-images.githubusercontent.com/57741609/160423634-eeb4a084-e66f-444b-b0e3-2372ba785558.png)

* A Implementação de **Login** e **Home** foi só para facilitar o teste/visualizações das criações de contas.

##
# Descrição do Projeto

A ideia do projeto consiste em um super app juntando todos os canais de vendas disponíveis na Bemol com a possibilidade de expandir para lojas terceiras também anunciarem seus produtos dentro do Bemall Shop.
No entanto, toda a navegação e processo de compra será feita de maneira fluída sem fazer distinção do canal de venda, o único momento que o usuário terá acesso a qual canal de venda, será na verificação se o produto está disponível para entrega/retirada  e em qual local, se houver. 

##
# C4-Model
### Camada 1
O Sistema como um todo terá que permitir que usuários comprem produtos de vendedores cadastrados no sistema.

<img width="741" alt="Captura de Tela 2022-03-28 às 23 56 31" src="https://user-images.githubusercontent.com/57741609/160530209-26ca68e8-a19f-4426-a812-3b8099d0844f.png">


##

### Camada 2
Durante a modelagem do problema eu vi que era necessário também ter uma aplicação para o vendedor, sendo ela um sistema web, para gerenciamento de produtos e pedidos.

<img width="726" alt="Captura de Tela 2022-03-28 às 23 43 45" src="https://user-images.githubusercontent.com/57741609/160528923-14620ad5-33c7-4dc2-b031-c97671bbcf4d.png">

##

### Camada 3
Nessa eu está definida apenas o container de **API Aplication**, pois é nele que está concentrada toda a lógica de negócio. A estratégia adotada é orientada a microserviços. Por isso, os componentes de conexão com o banco de dados não foram desenhados, já que ia mais poluir o diagrama do que auxiliar no entendimento.

<img width="902" alt="Captura de Tela 2022-03-28 às 23 50 07" src="https://user-images.githubusercontent.com/57741609/160529581-c476d7df-abf3-4591-8a93-64c98ec7295c.png">

##

### Camada 4
Não foi desenhada, pois não faz sentido desenhar toda as relações de classes/interfaces sem estar com todas as camadas acima bem definidas de acordo com o levantamento de requisitos do sistema.

##
# Design do Backend

O design do backend é modular orientada a microserviços. Pois além dessa estrutura permitir respeitar os princípios SOLID é de fácil compreensão e aprendizado. Além disso, tem uma facilidade de ser bem escalável.

<img width="477" alt="Captura de Tela 2022-03-29 às 00 25 24" src="https://user-images.githubusercontent.com/57741609/160532984-70fc634c-bd59-4c14-a695-84188144cc7c.png">


### 

### Design Mobile

O design do app é modular e por toda lógica estar implementada no backend não é necessário a camada de microserviços. A Lógica existente entre interface e regras de negócio é concentrada no controller, que basicamente só tem acesso a camada de repositories e aos atributos definidos na camada de entidades.

<img width="996" alt="Captura de Tela 2022-03-29 às 00 59 27" src="https://user-images.githubusercontent.com/57741609/160536560-53595c98-455c-43e1-8e47-e94d174f99ef.png">




