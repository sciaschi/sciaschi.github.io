<script setup lang="ts">
import { RouterLink, RouterView } from 'vue-router'
</script>

<template>
  <v-app color="black">
    <nav>
      <v-app-bar color="teal-darken-3">
        <template v-slot:prepend>
          <v-app-bar-title class="pl-4">Sean Ciaschi's Portfolio</v-app-bar-title>
        </template>

        <div class="nav-links">
          <RouterLink to="/">Home</RouterLink>
          <RouterLink to="/about">About</RouterLink>
          <RouterLink to="/projects">Projects</RouterLink>
          <RouterLink to="/contact">Contact Me</RouterLink>
        </div>

      </v-app-bar>
    </nav>
    <v-main class="app-container" style="background-color: #181818; color: white">
      <RouterView />
    </v-main>
  </v-app>
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

nav a {
  /* top | right | bottom | left */
  padding: 1rem 2rem 1rem 2rem;
  border-left: 1px solid var(--color-border);
  text-decoration: none;
  color: white;
}

nav a:first-of-type {
  border-left: none;
}

nav a.router-link-exact-active {
  color: yellow;
}

nav a.router-link-exact-active:hover {
  background-color: transparent;
}

.app-container {
  margin-top: 3rem;
  width: 100%;
}
</style>
