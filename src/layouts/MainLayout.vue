<template>
  <q-layout view="hHh Lpr lFf">
    <q-header elevated>
      <q-toolbar>
        <q-btn
          padding="none"
          flat
          icon="fas fa-ellipsis-v"
          aria-label="Menu"
          @click="drawer = !drawer"
        />
        <q-toolbar-title>Gu Caciolato</q-toolbar-title>
        <q-btn
          outline 
          flat 
          dense 
          icon="fab fa-vuejs"    
        ></q-btn>
        <q-btn 
          outline 
          flat 
          dense 
          icon="fab fa-node-js"    
        ></q-btn>
        <q-btn
          outline 
          flat 
          dense 
          icon="fas fa-guitar"    
        ></q-btn>
      </q-toolbar>
      <q-tabs v-model="tab">
          <q-tab name="portifolio" label="Portifólio" />
          <q-tab name="articles" label="Artigos" />
        </q-tabs>
      </q-header>

    <q-drawer 
      show-if-above
      v-model="drawer" 
      :mini="miniState"
      @mouseover="miniState = false"
      @mouseout="miniState = true"
      mini-to-overlay
    >
      <q-list>

        <EssentialLink
          v-for="link in essentialLinks"
          :key="link.title"
          v-bind="link"
        />
      </q-list>
    </q-drawer>

    <q-page-container>
      <router-view />
    </q-page-container>
  </q-layout>
</template>

<script>
import EssentialLink from "components/EssentialLink.vue";

const linksList = [
  {
    title: "Github",
    caption: "github.com/gucaciolato",
    icon: "fab fa-github",
    link: "https://github.com/gucaciolato",
  },
  {
    title: "Whatsapp",
    caption: "+55 (18) 98148-8133",
    icon: "fab fa-whatsapp",
    link: "https://wa.me/5518981488133",
  },
  {
    title: "LinkedIn",
    caption: "linkedin.com/in/gustavocaciolato",
    icon: "fab fa-linkedin",
    link: "https://linkedin.com/in/gustavocaciolato",
  },
  {
    title: "E-mail",
    caption: "caciolato@outlook.com",
    icon: "fas fa-envelope",
    link: "mailto:caciolato@outlook.com",
  },
];

import { defineComponent, ref } from "vue";

export default defineComponent({
  name: "MainLayout",

  components: {
    EssentialLink,
  },

  setup() {
    return {
      essentialLinks: linksList,
      drawer: ref(false),
      miniState: ref(true),
      tab: ref('images')
    };
  },
});
</script>
