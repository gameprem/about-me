<template>
  <section class="mb-4">
    <h2 class="section-title">Technical Skills</h2>
    <div class="grid grid-cols-1 md:grid-cols-2 gap-1">
      <div
        v-for="category in skillCategories"
        :key="category.name"
        class="bg-gray-50 p-1 rounded"
      >
        <h3 class="text-xs font-semibold text-gray-700 ">
          {{ category.name }}
        </h3>
        <div class="flex flex-wrap gap-0.5">
          <span v-for="skill in category.skills" :key="skill" class="skill-tag">
            {{ skill }}
          </span>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup lang="ts">
interface SkillCategory {
  name: string;
  skills: string[];
}

const skillCategories: SkillCategory[] = [
  {
    name: "Programming Languages",
    skills: ["Dart", "JavaScript/TypeScript", "Python", "Go"],
  },
  {
    name: "Front-end Development",
    skills: ["Flutter", "Vue.js", "Next.js", "React Native"],
  },
  {
    name: "Back-end Development",
    skills: ["ExpressJS", "NestJS", "Echo"],
  },
  {
    name: "Database & Caching",
    skills: ["MongoDB", "PostgreSQL", "Redis"],
  },
  {
    name: "DevOps & Infrastructure",
    skills: ["Docker", "Kafka", "Socket.IO"],
  },
];
</script>
