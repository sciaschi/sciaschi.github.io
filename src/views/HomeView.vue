<script setup lang="ts">
const meImg = new URL('@/assets/me.png', import.meta.url).href;
const headerImg = new URL('@/assets/home-header-bg.jpg', import.meta.url).href;

const skillsList = [
  "Laravel",
  "Vue 3",
  "Rest APIs",
  "HTML",
  "CSS",
  "Javascript",
  "Node.js",
  "MySQL"
]
</script>

<template>
  <v-sheet id="info-header" :style="`background: url(${headerImg}) no-repeat center;`">
    <div id="info-content">
      <v-img :src="meImg" rounded="circle" cover width="248" height="248" class="mx-15"></v-img>
      <v-container fluid id="description">
        Hello, my name is Sean Ciaschi! I’m a web developer who
        loves building things from the ground up. A lot of the time, you’ll find me hacking together
        websites, embedded systems, designing PCBs, or working on some other sort of electronics project.
        I’m especially into projects that blur the line between software and hardware and push the bounds of
        current technologies.
      </v-container>
    </div>
  </v-sheet>
  <v-container fluid>
    <v-row>
      <v-col>
        <v-card>
          <v-card-title class="pa-5" style="font-size:x-large;"><v-icon icon="mdi-account-school" /> Education</v-card-title>
          <v-card-text>
            <v-list>
              <v-list-item>
                Sullivan County Community College, Loch Sheldrake, NY — Game
                and Simulation Development
                <v-list-item-subtitle>August 2014 - June 2016</v-list-item-subtitle>
              </v-list-item>
            </v-list>
          </v-card-text>
        </v-card>
      </v-col>

      <v-col>
        <v-card>
          <v-card-title class="pa-5" style="font-size:x-large;"><v-icon icon="mdi-laptop" /> Skills</v-card-title>
          <v-card-text>
            <div class="d-flex ga-2">
                <v-chip v-for="(skill, index) in skillsList" :key="index">{{skill}}</v-chip>
            </div>
          </v-card-text>
        </v-card>
      </v-col>
    </v-row>
  </v-container>

</template>

<style>
#info-header {
  height: 500px;
  align-content: center;
}

#info-content {
  display: inline-flex;
}

#description {
  align-self: center;
  font-size: x-large;
  text-shadow: 0 1px black;
}
</style>
