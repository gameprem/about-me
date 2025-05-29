<template>
  <section>
    <h2 class="section-title">Languages</h2>
    <div class="flex flex-wrap">
      <span v-for="lang in languages" :key="lang.name" class="skill-tag">
        {{ lang.name }}: {{ lang.level }}
      </span>
    </div>
  </section>
</template>

<script setup lang="ts">
interface Language {
  name: string;
  level: string;
}

const languages: Language[] = [
  { name: "Thai", level: "Native" },
  { name: "English", level: "Intermediate" },
];
</script>
