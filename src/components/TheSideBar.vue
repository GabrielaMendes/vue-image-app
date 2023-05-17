<script setup>
import { inject } from 'vue';

const emits = defineEmits(["optionSelected"]);

const selectOption = (isColor) => {
  emits("optionSelected", isColor);
};

const isWithColor = inject("isWithColor");
</script>

<template>
  <v-navigation-drawer
    style="transform: translateX(0%);"
    :width="280"
    expand-on-hover
    rail
  >
    <v-list>
      <v-list-item
        prepend-avatar="src/assets/profile-pic.png"
        title="Gabriela Mendes"
        subtitle="notmyemail@gmail.com"
      ></v-list-item>
    </v-list>

    <v-divider></v-divider>

    <v-list density="compact" nav>
      <v-list-item
        prepend-icon="mdi-image"
        title="Color Gallery"
        value="color"
        :elevation="isWithColor ? 1 : 0"
        @click="selectOption(true)"
      ></v-list-item>
      <v-list-item
        prepend-icon="mdi-dialpad"
        title="Grayspace Gallery"
        value="color"
        :elevation="isWithColor ? 0 : 1"
        @click="selectOption(false)"
      ></v-list-item>
    </v-list>
  </v-navigation-drawer>
</template>
