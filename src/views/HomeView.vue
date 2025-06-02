<script setup lang="ts">
import { useDisplay } from 'vuetify'
import {computed} from "vue";

const meImg = new URL('@/assets/images/me.png', import.meta.url).href;
const headerImg = new URL('@/assets/images/home-header-bg.jpg', import.meta.url).href;
const skillsList = [
  "Laravel",
  "Vue 3",
  "Rest APIs",
  "HTML",
  "CSS",
  "Javascript",
  "Node.js",
  "MySQL",
  "Docker",
  "ExpressJS",
  "Git",
  "Linux",
  "MSSQL",
  "Microsoft Office",
  "TypeScript",
];

const jobHistoryList = [
  {
    title: "FasTrax Solutions, Rock Hill, NY — Web Developer",
    workedDates: "January 2017 - August 2019",
    description: "Developed Point of Sale (POS) and business management software using the Laravel PHP framework to support retail operations and backend administration.",
  },
  {
    title: "Greenshades Software, Remote — Junior Software Developer",
    workedDates: "August 2019 - October 2020",
    description: "Designed and developed an employee management system to streamline HR operations and general business workflows.",
  },
  {
    title: "Home Depot — Matamoras, PA — Overnight Stocker",
    workedDates: "October 2021 – March 2022",
    description: "Responsible for unloading, stocking, and organizing merchandise in a retail or warehouse environment during overnight hours. Ensures shelves are replenished and inventory is accurate, while maintaining a clean and safe workspace.",
  },
  {
    title: "Taxi Service, Big Run, PA — Driver",
    workedDates: "October 2021 – March 2022",
    description: "Provides transportation services to passengers, ensuring timely and safe travel to destinations. Responsibilities include navigating routes, maintaining vehicle cleanliness, and offering excellent customer service.",
  },
  {
    title: "Movate, Remote — Game Content Moderator",
    workedDates: "August 2022 – Present",
    description: "Review and evaluate user-submitted usernames to ensure compliance with community guidelines, terms of service, and content policies.",
  },
]

const { mdAndDown } = useDisplay()

// Timeline direction: vertical for md and smaller, horizontal otherwise
const timelineDirection = computed(() => mdAndDown.value ? 'vertical' : 'horizontal')
skillsList.sort();
</script>

<template>
  <v-sheet id="info-header" :style="`background: url(${headerImg}) no-repeat center;`">
    <div id="info-content">
      <v-img :src="meImg" rounded="circle" cover width="248" height="248" class="mx-15"></v-img>
      <v-container fluid id="description">
        Hello, my name is Sean Ciaschi! I’m a web developer who loves building things from the ground
        up. A lot of the time, you’ll find me hacking together websites, embedded systems, designing
        PCBs, or working on some other sort of electronics project. I’m especially into projects that
        blur the line between software and hardware and push the bounds of current technologies.
      </v-container>
    </div>
  </v-sheet>
  <v-container fluid>
    <v-row>
      <v-col cols="12" sm="6" md="6">
        <v-card height="200">
          <v-card-title class="pa-5" style="font-size:x-large;"><v-icon icon="mdi-account-school" /> Education</v-card-title>
          <v-card-text>
            <v-list>
              <v-list-item>
                Sullivan County Community College, Loch Sheldrake, NY — Game
                and Simulation Development
                <v-list-item-subtitle class="pt-1">Associates in Computer Science</v-list-item-subtitle>
                <v-list-item-subtitle class="py-3">August 2014 - June 2016</v-list-item-subtitle>
              </v-list-item>
            </v-list>
          </v-card-text>
        </v-card>
      </v-col>

      <v-col sm="6" md="6">
        <v-card height="200">
          <v-card-title class="pa-5" style="font-size:x-large;"><v-icon icon="mdi-laptop" /> Skills</v-card-title>
          <v-card-text>
            <div class="ga-2">
                <v-chip v-for="(skill, index) in skillsList" :key="index" class="ma-1 gradient-chip pointer">{{skill}}</v-chip>
            </div>
          </v-card-text>
        </v-card>
      </v-col>
    </v-row>
    <v-row>
      <v-col>
        <v-card>
          <v-card-title class="pa-5" style="font-size:x-large;"><v-icon icon="mdi-laptop" /> Job History</v-card-title>
          <v-card-text>
            <v-timeline :direction="timelineDirection">
              <v-timeline-item v-for="(job, index) in jobHistoryList" :key="index">
                <template v-slot:opposite>
                  {{job.workedDates}}
                </template>
                <div>
                  <div class="text-h6 pb-4">{{job.title}}</div>
                  <p>
                    {{job.description}}
                  </p>
                </div>
              </v-timeline-item>
            </v-timeline>
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

.gradient-chip {
  transition: background 500ms ease;
}

.gradient-chip::before {
  content: "";
  position: absolute;
  inset: 0;
  background: linear-gradient(45deg, #00695C, #B2DFDB);
  opacity: 0;
  transition: opacity 500ms ease;
  z-index: 0;
}

.gradient-chip:hover::before {
  opacity: 1;
}

.gradient-chip > * {
  position: relative;
  z-index: 1;
}

.v-timeline .v-timeline-divider__inner-dot {
  background: rgb(var(--v-theme-on-surface));
  transition: background 500ms ease;
}
.v-timeline .v-timeline-divider__inner-dot:hover {
  background: #00695C !important;
  transition: background 500ms ease;
}

.pointer {
  cursor: default;
}

@media(max-width: 1280px) {
  #info-header {
    height: auto;
    align-content: center;
  }

  #info-content {
    display: block;
  }
}

</style>
