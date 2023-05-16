<script setup>
  import TheSideBar from "@/components/TheSideBar.vue"
  import ImageGallery from "@/components/ImageGallery.vue"
</script>

<template>
  <v-app>
    <!-- Sidebar -->
    <TheSideBar />
    <v-main>
      <!-- Cards -->
      <ImageGallery />
    </v-main>
  </v-app>
</template>


