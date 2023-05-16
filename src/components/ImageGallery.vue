<script setup>
import ImageGalleryItem from './ImageGalleryItem.vue';
</script>

<template>
  <v-card class="mx-5 my-2 pa-3">
    <v-row>
      <v-col v-for="n in 200" :key="n" cols="4" sm="3" md="2" lg="1">
        <ImageGalleryItem :n="n" />
      </v-col>
    </v-row>
  </v-card>
</template>
