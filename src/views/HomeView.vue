<script setup lang="ts">
import {computed, onMounted} from "vue";
import { useDisplay } from 'vuetify'
import { gsap } from "gsap";

onMounted(() => {
  gsap.from('.gradient-chip', {
    opacity: 0,
    y: 20,
    scale: 0.9,
    duration: 0.4,
    ease: 'power2.out',
    stagger: 0.07
  })
});

const { mdAndDown } = useDisplay();
const timelineDirection = computed(() => mdAndDown.value ? 'vertical' : 'horizontal')
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
  "SQL",
  "Docker",
  "ExpressJS",
  "Git",
  "Linux",
  "Microsoft Office",
  "TypeScript",
  "Time Management",
  "Customer Service",
];

const jobHistoryList = [
  {
    id: "job-fastrax",
    title: "FasTrax Solutions, Rock Hill, NY — Web Developer",
    workedDates: "January 2017 - August 2019",
    description: "Developed Point of Sale (POS) and business management software using the Laravel PHP framework to support retail operations and backend administration.",
    skills: ["Laravel", "Rest APIs", "SQL", "Git", "HTML", "CSS", "Javascript", "Microsoft Office"],
  },
  {
    id: "job-greenshades",
    title: "Greenshades Software, Remote — Junior Software Developer",
    workedDates: "August 2019 - October 2020",
    description: "Designed and developed an employee management system to streamline HR operations and general business workflows.",
    skills: ["Rest APIs", "SQL", "Git", "HTML", "CSS", "TypeScript", "Microsoft Office"],
  },
  {
    id: "job-homedepot",
    title: "Home Depot — Matamoras, PA — Overnight Stocker",
    workedDates: "October 2021 – March 2022",
    description: "Responsible for unloading, stocking, and organizing merchandise in a retail or warehouse environment during overnight hours. Ensures shelves are replenished and inventory is accurate, while maintaining a clean and safe workspace.",
    skills: ["Customer Service"],
  },
  {
    id: "job-taxidriver",
    title: "Taxi Service, Big Run, PA — Driver",
    workedDates: "June 2022 – August 2022",
    description: "Provides transportation services to passengers, ensuring timely and safe travel to destinations. Responsibilities include navigating routes, maintaining vehicle cleanliness, and offering excellent customer service.",
    skills: ["Time Management", "Customer Service"],
  },
  {
    id: "job-movate",
    title: "Movate, Remote — Game Content Moderator",
    workedDates: "August 2022 – Present",
    description: "Review and evaluate user-submitted usernames to ensure compliance with community guidelines, terms of service, and content policies.",
    skills: ["Time Management", "Customer Service", "Microsoft Office"],
  },
];

skillsList.sort();


function scaleDown(event: Event) {
  gsap.to(event.currentTarget, {
    scale: 1,
    duration: 0.3,
    ease: 'power2.inOut'
  });

  resetJobHighlights();
}

function handleSkillHover(event: Event, skill: string) {
  gsap.to(event.currentTarget, {
    scale: 1.1,
    duration: 0.3,
    ease: 'power2.out'
  });

  gsap.utils.toArray<HTMLElement>('.job-entry').forEach(el => {
    const job = jobHistoryList.find(j => j.id === el.dataset.id);
    const dot = el.closest('.v-timeline-item')?.querySelector('.v-timeline-divider__inner-dot');

    if (job && job.skills?.includes(skill)) {
      gsap.to(el, {
        opacity: 1,
        scale: 1.02,
        duration: 0.2
      });

      if (dot) {
        gsap.to(dot, {
          backgroundColor: '#00695C',
          scale: 1.2,
          duration: 0.2
        });
      }
    } else {
      gsap.to(el, {
        opacity: 0.4,
        scale: 1,
        duration: 0.2
      });

      if (dot) {
        gsap.to(dot, {
          backgroundColor: 'rgb(var(--v-theme-on-surface))',
          scale: 1,
          duration: 0.2
        });
      }
    }
  });
}

function resetJobHighlights() {
  gsap.to('.job-entry', { opacity: 1, scale: 1, duration: 0.2 });

  gsap.utils.toArray<HTMLElement>('.v-timeline-divider__inner-dot').forEach(dot => {
    gsap.to(dot, {
      backgroundColor: 'rgb(var(--v-theme-on-surface))',
      scale: 1,
      duration: 0.2
    });
  });
}
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
        <v-card  id="edu-card" height="200">
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
        <v-card id="skills-card" height="200">
          <v-card-title class="pa-5" style="font-size:x-large;"><v-icon icon="mdi-laptop" /> Skills</v-card-title>
          <v-card-text>
            <div class="ga-2">
                <v-chip v-for="(skill, index) in skillsList"
                        :key="index"
                        class="ma-1 gradient-chip pointer"
                        @mouseenter="(e: Event) => handleSkillHover(e, skill)"
                        @mouseleave="scaleDown">
                  {{skill}}
                </v-chip>
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
              <v-timeline-item
                v-for="(job, index) in jobHistoryList"
                :key="index"
              >
                <div class="job-entry" :data-id="job.id">
                  <div class="text-caption text-grey pb-1">{{ job.workedDates }}</div>
                  <div class="text-h6 pb-2">{{ job.title }}</div>
                  <p id="job-description">{{ job.description }}</p>
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
  font-family: "Inter", serif;
}

#description {
  align-self: center;
  font-family: "Inter", serif;
  font-size: x-large;
  text-shadow: 0 1px black;
}

#job-description {
  font-family: "Inter", serif;
}

.gradient-chip {
  font-family: "Inter", serif;
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

.pointer {
  cursor: default;
}

.text-caption {
  font-size: 0.875rem;
  color: gray;
}

@media(max-width: 1280px) {
  #info-header {
    height: auto;
    align-content: center;
  }

  #info-content {
    display: block;
  }

  #skills-card {
    height:auto !important;
  }

  #edu-card {
    height:auto !important;
  }
}
</style>
