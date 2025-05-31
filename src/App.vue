<script setup lang="ts">
import { RouterLink, RouterView } from 'vue-router'
</script>

<template>
  <v-layout>
    <v-app-bar title="Sean Ciaschi's Portfolio" color="teal-darken-3">
        <div class="nav-links">
          <RouterLink to="/"><v-icon icon="mdi-home"></v-icon>Home</RouterLink>
          <a href="https://www.linkedin.com/in/sean-ciaschi-1b0b108b/" target="_blank"><v-icon icon="mdi-linkedin"></v-icon> LinkedIn</a>
          <a href="https://github.com/sciaschi" target="_blank"><v-icon icon="mdi-github"></v-icon> GitHub</a>
          <RouterLink to="/projects"><v-icon icon="mdi-hammer"></v-icon> Projects</RouterLink>
        </div>
    </v-app-bar>

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
  color: white;
}

.nav-links a:first-of-type {
  border-left: none;
}

.nav-links a.router-link-exact-active {
  color: yellow;
}

.nav-links a.router-link-exact-active:hover {
  background-color: transparent;
}
</style>
