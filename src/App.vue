<script setup>
  import TheSideBar from "@/components/TheSideBar.vue"
  import ImageGallery from "@/components/ImageGallery.vue"
  import { ref } from "vue";

  const isWithColor = ref(true);

  const onOptionSelected = (isColor) =>  {
    isWithColor.value = isColor;
  }
</script>

<template>
  <v-app>
    <!-- Sidebar -->
    <TheSideBar @option-selected="onOptionSelected" />
    <v-main>
      <!-- Cards -->
      <ImageGallery :isWithColor="isWithColor" />
    </v-main>
  </v-app>
</template>


