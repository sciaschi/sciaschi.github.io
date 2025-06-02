<script setup lang="ts">
import { RouterLink, RouterView } from 'vue-router'
import {useDisplay} from "vuetify/framework";
import {computed, ref} from "vue";
const { mdAndDown } = useDisplay()

// Timeline direction: vertical for md and smaller, horizontal otherwise
const isMobile = computed(() => mdAndDown.value)

const drawer = ref(false)
</script>

<template>
  <v-layout>
    <v-app-bar title="Sean Ciaschi's Portfolio" color="teal-darken-3">
      <template v-slot:prepend>
        <v-app-bar-nav-icon v-if="isMobile" @click.stop="drawer = !drawer"></v-app-bar-nav-icon>
      </template>

      <div class="nav-links" v-if="!isMobile">
        <RouterLink to="/" activeClass="text-white"><v-icon icon="mdi-home"></v-icon> Home</RouterLink>
        <a href="https://www.linkedin.com/in/sean-ciaschi-1b0b108b/" target="_blank"><v-icon icon="mdi-linkedin"></v-icon> LinkedIn</a>
        <a href="https://github.com/sciaschi" target="_blank"><v-icon icon="mdi-github"></v-icon> GitHub</a>
      </div>
    </v-app-bar>
    <v-navigation-drawer  v-if="isMobile" v-model="drawer" location="left">
      <v-list>
       <v-list-item> <RouterLink to="/"><v-icon icon="mdi-home"></v-icon>Home</RouterLink></v-list-item>
        <v-list-item><a href="https://www.linkedin.com/in/sean-ciaschi-1b0b108b/" target="_blank"><v-icon icon="mdi-linkedin"></v-icon> LinkedIn</a></v-list-item>
        <v-list-item><a href="https://github.com/sciaschi" target="_blank"><v-icon icon="mdi-github"></v-icon> GitHub</a></v-list-item>
      </v-list>
    </v-navigation-drawer>

    <v-main>
      <v-container fluid class="pa-0">
        <RouterView />
      </v-container>
    </v-main>
  </v-layout>
</template>

<style scoped>
.nav-links {
  position: absolute;
  left: 50%;
  transform: translateX(-50%);
  display: flex;
  align-items: center;
  padding: 30px;
}

.nav-links a {
  /* top | right | bottom | left */
  padding: 1rem 2rem 1rem 2rem;
  border-left: 1px solid rgba(166, 166, 166, 0.5);
  text-decoration: none;
  color: #B2DFDB;
}

.nav-links a:first-of-type {
  border-left: none;
}

.nav-links a:active {
  color: #ECEFF1;
}

.nav-links a:hover {
  color: #1DE9B6;
}
</style>
