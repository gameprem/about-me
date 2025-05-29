<template>
  <section class="mb-6">
    <h2 class="section-title">Professional Experience</h2>
    <div
      v-for="(exp, idx) in experiences"
      :key="exp.company + exp.period"
      class="mb-4"
    >
      <div class="flex justify-between items-start mb-2">
        <div>
          <h3 class="text-lg font-bold text-gray-800">{{ exp.position }}</h3>
          <div class="text-[var(--theme-color)] font-medium text-sm">
            {{ exp.company }}
          </div>
        </div>
        <div class="text-gray-600 text-right text-sm">
          <div>{{ exp.location }}</div>
          <div class="italic">{{ exp.period }}</div>
        </div>
      </div>
      <ul class="list-disc list-inside text-gray-700 text-sm space-y-1">
        <li v-for="(detail, i) in exp.details" :key="i">{{ detail }}</li>
      </ul>
    </div>
  </section>
</template>

<script setup lang="ts">
interface ExperienceItem {
  position: string;
  company: string;
  location: string;
  period: string;
  details: string[];
}

const experiences: ExperienceItem[] = [
  {
    position: "Full-Stack Developer",
    company: "Pobpa Co., Ltd.",
    location: "Bangkok",
    period: "January 2024 – Present",
    details: [
      "Led the migration of legacy systems to a modern microservices architecture using NestJS and Docker",
      "Developed and maintained scalable RESTful APIs to support business growth and new product features",
      "Collaborated with UI/UX designers to deliver responsive web applications using Vue.js",
      "Integrated third-party payment and notification services to enhance platform capabilities",
      "Mentored junior developers and conducted code reviews to ensure code quality and best practices",
    ],
  },
  {
    position: "Full-Stack Developer",
    company: "START APPLICATION Co., Ltd.",
    location: "Udon Thani",
    period: "January 2021 – December 2023",
    details: [
      "Designed and implemented database schemas to support scalable business logic",
      "Developed RESTful APIs using ExpressJS and NestJS",
      "Built responsive web applications with Vue.js",
      "Developed cross-platform mobile apps using Flutter, integrating real-time features",
    ],
  },
  {
    position: "Full-Stack Developer",
    company: "Quinl (Thailand) Co., Ltd.",
    location: "Udon Thani",
    period: "January 2020 – December 2020",
    details: [
      "Architected and maintained database structures for high-availability systems",
      "Created RESTful services with ExpressJS/NestJS to power web and mobile clients",
      "Developed web interfaces using Vue.js and optimized performance",
      "Delivered mobile solutions with Flutter, leveraging Redis for caching",
    ],
  },
];
</script>
