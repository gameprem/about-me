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
      <label
        class="bg-white px-4 py-3 rounded-xl shadow-lg flex items-center cursor-pointer"
      >
        <span class="mr-2 text-sm text-gray-700">Image:</span>
        <input
          type="file"
          accept="image/*"
          @change="onImageChange"
          class="hidden"
        />
        <span class="bg-gray-200 px-3 py-1 rounded text-xs">Select image</span>
      </label>
      <button
        v-if="imageData"
        @click.stop="clearImage"
        class="bg-[var(--theme-color)] text-white px-6 py-3 rounded-xl flex items-center hover:opacity-90 transition-colors duration-200 shadow-lg"
      >
        <DocumentIcon class="h-5 w-5 mr-2" />
        Clear Image
      </button>
      <button
        @click="handlePrint"
        class="bg-[var(--theme-color)] text-white px-6 py-3 rounded-xl flex items-center hover:opacity-90 transition-colors duration-200 shadow-lg"
      >
        <PrinterIcon class="h-5 w-5 mr-2" />
        Print CV
      </button>
    </div>

    <!-- Header -->
    <div
      class="p-8 bg-gradient-to-r from-[var(--theme-color)] rounded-t-2xl to-[var(--theme-color)] text-white flex items-center gap-8"
    >
      <div v-if="imageData" class="flex-shrink-0">
        <img
          :src="imageData"
          alt="Profile"
          class="w-28 h-28 object-cover rounded-full border-4 border-white shadow-lg"
        />
      </div>
      <div>
        <h1 class="text-3xl font-bold mb-3">Nitivat Vorasan (Prem)</h1>
        <div class="space-y-1 text-white/90 text-sm">
          <p class="flex items-center">
            <span class="font-medium w-16">Phone:</span>
            <span>+66 91-680-7533</span>
          </p>
          <p class="flex items-center">
            <span class="font-medium w-16">Email:</span>
            <a
              href="mailto:nitivatkps@gmail.com"
              class="hover:text-white transition-colors"
              >nitivatkps@gmail.com</a
            >
          </p>
          <p class="flex items-center">
            <span class="font-medium w-16">Address:</span>
            <span
              >333 Moo 9 Na Chan, Mueang Kalasin District, Kalasin 46000,
              Thailand</span
            >
          </p>
          <p class="flex items-center">
            <span class="font-medium w-16">LinkedIn:</span>
            <a
              href="https://www.linkedin.com/in/nitivatvorasan"
              class="hover:text-white transition-colors"
              >linkedin.com/in/nitivatvorasan</a
            >
          </p>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup lang="ts">
import { PrinterIcon, DocumentIcon } from "@heroicons/vue/24/outline";
import { ref, onMounted } from "vue";

const themeColor = ref("#2563eb"); // Default blue-600
const imageData = ref<string | null>(null);

onMounted(() => {
  const savedColor = localStorage.getItem("themeColor");
  if (savedColor) {
    themeColor.value = savedColor;
    document.documentElement.style.setProperty(
      "--theme-color",
      themeColor.value
    );
    document.documentElement.style.setProperty(
      "--theme-color-light",
      `${themeColor.value}10`
    );
  }
  const savedImage = localStorage.getItem("profileImage");
  if (savedImage) {
    imageData.value = savedImage;
  }
});

const handlePrint = () => {
  window.print();
};

const updateThemeColor = (e: Event) => {
  const input = e.target as HTMLInputElement;
  themeColor.value = input.value;
  localStorage.setItem("themeColor", themeColor.value);
  document.documentElement.style.setProperty("--theme-color", themeColor.value);
  document.documentElement.style.setProperty(
    "--theme-color-light",
    `${themeColor.value}10`
  );
};

const onImageChange = (e: Event) => {
  const input = e.target as HTMLInputElement;
  if (input.files && input.files[0]) {
    const reader = new FileReader();
    reader.onload = (event) => {
      imageData.value = event.target?.result as string;
      localStorage.setItem("profileImage", imageData.value);
    };
    reader.readAsDataURL(input.files[0]);
  }
};

const clearImage = () => {
  imageData.value = null;
  localStorage.removeItem("profileImage");
};
</script>
