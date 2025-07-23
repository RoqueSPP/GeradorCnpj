# **Uso de Variáveis de Ambiente no Cypress com Cypress.config()**
## **📌 O que são variáveis de ambiente no Cypress?**
Variáveis de ambiente são usadas para armazenar informações reutilizáveis, como URLs, tokens ou configurações específicas do ambiente de teste. No Cypress, é possível acessá-las através do método Cypress.config('nomeDaVariavel').

-----
## **🛠️ Configurando no cypress.config.js**
Você pode definir uma variável personalizada dentro da configuração do Cypress. Exemplo:

js

const { defineConfig } = require("cypress");

module.exports = defineConfig({

`  `e2e: {

`    `setupNodeEvents(on, config) {

`      `// Aqui você pode adicionar eventos personalizados do Node, se necessário.

`    `},

`    `UrlBase: 'google.com.br' // Variável personalizada para ser usada nos testes

`  `},

});

-----
## **🚀 Usando a variável no teste**
Agora que você configurou a variável UrlBase, pode usá-la dentro dos testes com Cypress.config().
### **Exemplo de uso:**
js


describe('Exemplo de uso da variável de ambiente', () => {

`  `it('Acessa o site usando a variável configurada', () => {

`    `cy.visit(`https://${Cypress.config('UrlBase')}`); // Acessa www.google.com.br

`    `cy.log(Cypress.config('UrlBase')); // Exibe "google.com.br" no log do teste

`  `});

});

-----
## **💡 Dica: Usando interpolação de strings**
Para concatenar variáveis com strings, utilize **template literals** (crase ` ao invés de aspas simples ' ou duplas "). Coloque a variável dentro de ${}:

js

![ref1]Copiar![ref2]Editar

const url = `https://${Cypress.config('UrlBase')}`;

Assim, o Cypress interpretará corretamente o valor da variável como parte da string.

-----
## **✅ Resultado**
Ao rodar o teste, o Cypress irá:

1. Carregar a configuração da variável UrlBase.
1. Utilizar essa URL no comando cy.visit.
1. Imprimir o valor no log com cy.log.
