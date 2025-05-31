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
  "MySQL",
  "Docker",
  "ExpressJS",
  "Git",
  "Linux",
  "MSSQL",
  "Microsoft Office",
  "TypeScript",
];

skillsList.sort();
</script>

<template>
  <v-sheet id="info-header" :style="`background: url(${headerImg}) no-repeat center;`">
    <div id="info-content">
      <v-img :src="meImg" rounded="circle" cover width="248" height="248" class="mx-15"></v-img>
      <v-container fluid id="description">
        Hello, my name is Sean Ciaschi! I’m a web developer wholoves building things from the ground
        up. A lot of the time, you’ll find me hacking together websites, embedded systems, designing
        PCBs, or working on some other sort of electronics project. I’m especially into projects that
        blur the line between software and hardware and push the bounds of current technologies.
      </v-container>
    </div>
  </v-sheet>
  <v-container fluid>
    <v-row>
      <v-col cols="6">
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

      <v-col cols="6">
        <v-card>
          <v-card-title class="pa-5" style="font-size:x-large;"><v-icon icon="mdi-laptop" /> Skills</v-card-title>
          <v-card-text>
            <div class="ga-2">
                <v-chip v-for="(skill, index) in skillsList" :key="index" class="ma-1">{{skill}}</v-chip>
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
            <v-timeline direction="horizontal">
              <v-timeline-item>
                <template v-slot:opposite>
                  January 2017 - August 2019
                </template>
                <div>
                  <div class="text-h6 pb-4">FasTrax Solutions, Rock Hill, NY — Web Developer</div>
                  <p>
                    Developed Point of Sale (POS) and business management software using
                    the Laravel PHP framework to support retail operations and backend
                    administration.
                  </p>
                </div>
              </v-timeline-item>

              <v-timeline-item>
                <template v-slot:opposite>
                  August 2019 - October 2020
                </template>
                <div>
                  <div class="text-h6 pb-4">Greenshades Software, Remote — Junior Software Developer</div>
                  <p>
                    Designed and developed an employee management system to
                    streamline HR operations and general business workflows.
                  </p>
                </div>
              </v-timeline-item>

              <v-timeline-item>
                <template v-slot:opposite>
                  October 2021 – March 2022
                </template>
                <div>
                  <div class="text-h6 pb-4">Home Depot, Matamoras, PA — Overnight Freight Associate</div>
                  <p>
                    Responsible for unloading, stocking, and organizing merchandise in a retail or
                    warehouse environment during overnight hours. Ensures shelves are replenished
                    and inventory is accurate, while maintaining a clean and safe workspace.
                  </p>
                </div>
              </v-timeline-item>
              <v-timeline-item>
                <template v-slot:opposite>
                  June 2022 – August 2022
                </template>
                <div>
                  <div class="text-h6 pb-4">Taxi Service, Big Run, PA — Driver</div>
                  <p>
                    Provides transportation services to passengers, ensuring timely and safe travel
                    to destinations. Responsibilities include navigating routes, maintaining vehicle
                    cleanliness, and offering excellent customer service.
                  </p>
                </div>
              </v-timeline-item>
              <v-timeline-item>
                <template v-slot:opposite>
                  August 2022 – Present
                </template>
                <div>
                  <div class="text-h6 pb-4">Movate, Remote — Game Content Moderator</div>
                  <p>
                    Review and evaluate user-submitted usernames to ensure
                    compliance with community guidelines, terms of service, and content
                    policies.
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
</style>
