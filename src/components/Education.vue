<template>
  <section class="mb-6">
    <h2 class="section-title">Education</h2>
    <div v-for="(edu, idx) in educations" :key="idx" class="mb-3">
      <div class="flex justify-between items-start">
        <div>
          <h3 class="text-lg font-bold text-gray-800">{{ edu.degree }}</h3>
          <div class="text-[var(--theme-color)] text-sm">
            {{ edu.institution }}
          </div>
        </div>
        <div class="text-gray-600 text-right text-sm">{{ edu.years }}</div>
      </div>
      <p v-if="edu.gpa" class="text-gray-700 text-sm mt-1">
        GPA: {{ edu.gpa }}
      </p>
    </div>
  </section>
</template>

<script setup lang="ts">
type Education = {
  degree: string;
  institution: string;
  years: string;
  gpa?: string;
};

const educations: Education[] = [
  {
    degree: "Bachelor of Education in Computer Education",
    institution: "Rajabhat Maha Sarakham University, Thailand",
    years: "2016 – 2021",
    gpa: "3.88 / 4.00 (First Class Honours)",
  },
  {
    degree: "Science–Mathematics Program",
    institution: "Kalasinpittayasan School, Kalasin, Thailand",
    years: "2011 – 2016",
  },
];
</script>
