<template>
  <q-layout view="lHh Lpr lFf">
    <q-header elevated>
      <q-toolbar>
        <q-btn
          ref="menuBtn"
          flat
          dense
          round
          icon="menu"
          aria-label="Menu"
          @click="toggleLeftDrawer"
        />
        <q-toolbar-title ref="toolbarTitle"> Shepherd App </q-toolbar-title>

        <div>Quasar v{{ $q.version }}</div>
      </q-toolbar>
    </q-header>

    <q-drawer v-model="leftDrawerOpen" show-if-above bordered>
      <q-list>
        <q-item-label header> Essential Links </q-item-label>

        <EssentialLink
          v-for="link in linksList"
          :key="link.title"
          v-bind="link"
          :class="{
            'docs-link': link.title === 'Docs',
            'github-link': link.title === 'Github',
            'forum-link': link.title === 'Forum',
          }"
        />
      </q-list>
    </q-drawer>

    <q-page-container>
      <router-view />
    </q-page-container>
  </q-layout>
</template>

<script setup>
import { ref, onMounted } from "vue";
import EssentialLink from "components/EssentialLink.vue";
import Shepherd from "shepherd.js"; // Importando o Shepherd
import "shepherd.js/dist/css/shepherd.css"; // Importar o CSS do Shepherd

defineOptions({
  name: "MainLayout",
});

const linksList = [
  {
    title: "Docs",
    icon: "school",
    link: "https://quasar.dev",
  },
  {
    title: "Github",
    icon: "code",
    link: "https://github.com/quasarframework",
  },
  {
    title: "Forum",
    icon: "record_voice_over",
    link: "https://forum.quasar.dev",
  },
];

const leftDrawerOpen = ref(false);

function toggleLeftDrawer() {
  leftDrawerOpen.value = !leftDrawerOpen.value;
}

// Criando o tour com Shepherd
const createTour = () => {
  const tour = new Shepherd.Tour({
    useModalOverlay: true, // Usando a função que enfatiza o 'element' que esta contido no 'attachTo'
    defaultStepOptions: {
      classes: "shadow-md bg-purple-dark",
      scrollTo: true, // Usando 'scrollTo: true' ele permite ao rolar a tela que o tour, scroll junto.
    },
  });

  // Definindo os passos do tour
  tour.addStep({
    id: "menu-btn",
    text: "Esse botão abre o <strong>Menu Lateral</strong>.",
    attachTo: {
      element: ".q-btn",
      on: "top",
    },
    buttons: [
      {
        text: "Próximo",
        action: tour.next,
      },
    ],
  });

  tour.addStep({
    id: "docs",
    text:
      "Aqui você sera redirecionado para a <strong>Documentação Oficial</strong> do Quasar.",
    attachTo: {
      element: ".docs-link",
      on: "bottom",
    },
    buttons: [
      {
        text: "Próximo",
        action: tour.next,
      },
    ],
  });

  tour.addStep({
    id: "github",
    text: "Aqui você sera redirecionado para a <strong>GitHub</strong> do Quasar.",
    attachTo: {
      element: ".github-link",
      on: "right",
    },
    buttons: [
      {
        text: "Próximo",
        action: tour.next,
      },
    ],
  });
  tour.addStep({
    id: "forum",
    text:
      "Aqui você sera redirecionado para a <strong>Forum Oficial</strong> da aplicação.",
    attachTo: {
      element: ".forum-link",
      on: "left",
    },
    buttons: [
      {
        text: "Próximo",
        action: tour.next,
      },
      {
        text: "Sair",
        action: tour.back,
      },
    ],
  });

  tour.add;

  return tour;
};

// Configurar o tour quando o componente estiver montado
onMounted(() => {
  const tour = createTour();
  tour.start(); // Inicia o tour automaticamente
});
</script>
