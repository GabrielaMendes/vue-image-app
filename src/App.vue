<script setup>
import TheSideBar from "@/components/TheSideBar.vue"
import TheAppBar from "@/components/TheAppBar.vue"
import ImageGallery from "@/components/ImageGallery.vue"
import { useDisplay } from 'vuetify'
import { ref } from "vue";

const isWithColor = ref(true);

const onOptionSelected = (isColor) =>  {
  isWithColor.value = isColor;
}

const { mdAndUp } = useDisplay()
</script>

<template>
  <v-app>
    <!-- Sidebar -->
    <TheSideBar v-if="mdAndUp" @option-selected="onOptionSelected" />
    <!-- AppBar -->
    <TheAppBar v-else @option-selected="onOptionSelected" />
    <v-main>
      <!-- Cards -->
      <ImageGallery :isWithColor="isWithColor" />
    </v-main>
  </v-app>
</template>


