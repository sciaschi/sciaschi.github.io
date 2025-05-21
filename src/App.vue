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
        </div>

      </v-app-bar>
    </nav>
    <v-main>
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
  gap: 1rem;
}

nav a {
  padding: 0 1rem;
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
</style>
