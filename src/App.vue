<script setup lang="ts">
import Header from "./components/Header.vue";
import ProfessionalSummary from "./components/ProfessionalSummary.vue";
import TechnicalSkills from "./components/TechnicalSkills.vue";
import Experience from "./components/Experience.vue";
import Education from "./components/Education.vue";
import Languages from "./components/Languages.vue";
</script>

<template>
  <div class="min-h-screen bg-gray-50 py-8 px-4">
    <div
      class="max-w-4xl mx-auto bg-white shadow-xl rounded-2xl overflow-hidden"
    >
      <Header />
      <div class="p-8">
        <ProfessionalSummary />
        <div class="border-t border-dashed border-gray-200"></div>
        <TechnicalSkills />
        <div class="border-t border-dashed border-gray-200"></div>
        <Experience />
        <div class="border-t border-dashed border-gray-200"></div>
        <Education />
        <div class="border-t border-dashed border-gray-200"></div>
        <Languages />
      </div>
    </div>
  </div>
</template>
