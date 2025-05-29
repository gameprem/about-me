<script setup lang="ts">
import { PrinterIcon } from '@heroicons/vue/24/outline'
import { ref } from 'vue'

const themeColor = ref('#2563eb') // Default blue-600

const handlePrint = () => {
  window.print()
}

const updateThemeColor = (e: Event) => {
  const input = e.target as HTMLInputElement
  themeColor.value = input.value
  document.documentElement.style.setProperty('--theme-color', themeColor.value)
  document.documentElement.style.setProperty('--theme-color-light', `${themeColor.value}10`)
}
</script>

<template>
  <div>
    <div class="no-print fixed top-6 right-6 flex gap-2">
      <label class="bg-white px-4 py-3 rounded-xl shadow-lg flex items-center">
        <span class="mr-2 text-sm text-gray-700">Theme:</span>
        <input 
          type="color" 
          :value="themeColor"
          @input="updateThemeColor"
          class="w-8 h-8 rounded cursor-pointer"
        />
      </label>
      <button 
        @click="handlePrint"
        class="bg-[var(--theme-color)] text-white px-6 py-3 rounded-xl flex items-center hover:opacity-90 transition-colors duration-200 shadow-lg"
      >
        <PrinterIcon class="h-5 w-5 mr-2" />
        Print CV
      </button>
    </div>

    <!-- Header -->
    <div class="p-8 bg-gradient-to-r from-[var(--theme-color)] to-[var(--theme-color)] text-white">
      <h1 class="text-3xl font-bold mb-3">Nitivat Vorasan (Prem)</h1>
      <div class="space-y-1 text-white/90 text-sm">
        <p class="flex items-center">
          <span class="font-medium w-16">Phone:</span>
          <span>+66 91-680-7533</span>
        </p>
        <p class="flex items-center">
          <span class="font-medium w-16">Email:</span>
          <a href="mailto:nitivatkps@gmail.com" class="hover:text-white transition-colors">nitivatkps@gmail.com</a>
        </p>
        <p class="flex items-center">
          <span class="font-medium w-16">Address:</span>
          <span>333 Moo 9 Na Chan, Mueang Kalasin District, Kalasin 46000, Thailand</span>
        </p>
        <p class="flex items-center">
          <span class="font-medium w-16">LinkedIn:</span>
          <a href="https://www.linkedin.com/in/nitivatvorasan" class="hover:text-white transition-colors">linkedin.com/in/nitivatvorasan</a>
        </p>
      </div>
    </div>
  </div>
</template>