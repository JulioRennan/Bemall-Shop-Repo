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
<!--te-->

# Pontos cumpridos do desafio:
- [x] Nome ao projeto
- [x] Implementação única que permita cadastro do usuário.
- [x] Instruções de uso para execução do projeto.  
- [ ] Diagrama C4
- [ ] Design da solução.
- [x] Questionário respondido em .txt
##

# Setup do Projeto

O projeto foi divido em 2 componentes principais: o Backend reposável por processar toda a lógica de criação de conta/autenticação. E o Mobile é a interface que permite o usuário criar/autenticar usuários. O projeto deve funcionar independente do editor de texto usado, mas eu recomento utilizar o  [Visual Studio Code](https://code.visualstudio.com/download)

### Backend
A implentação é uma API REST simples que necessita realizar as instalações das seguintes ferramentas para funcionar:
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

Após realizar instalar todas as ferramentas execute os seguintes passos:
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


