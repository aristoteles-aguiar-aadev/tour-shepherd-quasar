# Projeto: Tour Interativo com Quasar e Shepherd.js

Este projeto é uma aplicação web desenvolvida com o framework **Quasar**, utilizando a biblioteca **Shepherd.js** para criar um tour interativo guiado, ajudando os usuários a navegar e compreender as principais funcionalidades da aplicação.

## Funcionalidades

- **Tour Guiado**: O projeto inclui um tour interativo que orienta os usuários sobre as funcionalidades mais importantes da interface.
- **Personalização de Estilos**: Estilos customizados foram aplicados, alinhados à identidade visual da marca, com destaque para os botões que utilizam a cor #00995D.
- **Elementos Interativos**: Durante o tour, alguns elementos foram configurados para serem informativos, mas não interativos, garantindo uma experiência guiada e eficiente.
- **Componentes Vue.js**: O tour foi implementado de forma modular e extensível, aproveitando o sistema de componentes do Quasar e Vue.js.

## Tecnologias Utilizadas

- **[Quasar Framework](https://quasar.dev/docs)**: Um poderoso framework baseado em Vue.js para criação de aplicações responsivas e de alta performance.
- **[Shepherd.js](https://github.com/shipshapecode/vue-shepherd)**: Biblioteca de tours interativos utilizada para guiar o usuário pelas principais funcionalidades da aplicação.

## Requisitos

Antes de iniciar o projeto, certifique-se de que seu ambiente de desenvolvimento está configurado com os seguintes requisitos:

- **Node.js** (>= 12.22.1)
- **Quasar CLI**

Para instalar o Quasar CLI:
# shepherd-app (quasar-shepherd)

## Instalando as dependências
```bash
yarn
# or
npm install
```

### Iniciar a aplicação em modo de desenvolvimento.
```bash
quasar dev
# or
yarn quasar dev
```

### Lint the files
```bash
yarn lint
# or
npm run lint
```

### Format the files
```bash
yarn format
# or
npm run format
```

### Build the app for production
```bash
quasar build
```

## Implementação do Tour Interativo

O tour interativo foi implementado utilizando a **Shepherd.js** integrada ao Vue.js. Para mais informações sobre como usar e configurar a biblioteca, consulte a [documentação oficial da Shepherd.js](https://docs.shepherdjs.dev/guides/usage/).

A biblioteca foi integrada de forma que o tour abranja as principais funcionalidades da aplicação, como a navegação entre as abas "Meu Plano" e "Minha Saúde", com destaque para componentes como assistente virtual, guias médicas, agendamento de consultas, entre outros.

### Exemplo de Uso

No arquivo principal da sua aplicação, você pode configurar o Shepherd.js assim:

```javascript
import { createApp } from 'vue';
import App from './App.vue';
import { createQuasar } from 'quasar';
import VueShepherd from 'vue-shepherd';

// Importando os estilos do Shepherd.js
import 'shepherd.js/dist/css/shepherd.css';

const app = createApp(App);

// Configuração do Quasar e Shepherd.js
app.use(createQuasar());
app.use(VueShepherd);

app.mount('#app');
```

Para detalhes sobre como configurar os tours passo a passo, consulte a [documentação da Shepherd.js](https://docs.shepherdjs.dev/guides/usage/).

## Documentação

- [Documentação do Quasar Framework](https://quasar.dev/docs)
- [Documentação da Shepherd.js](https://docs.shepherdjs.dev/guides/usage/)

## Contribuindo

Contribuições são bem-vindas! Se você encontrar algum problema ou tiver sugestões para melhorar este projeto, sinta-se à vontade para abrir uma issue ou enviar um pull request.

