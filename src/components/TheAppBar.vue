<script setup>
const emits = defineEmits(["optionSelected"]);

const selectOption = (isColor) => {
  emits("optionSelected", isColor);
};
</script>

<template>
  <v-app-bar color="white">
    <v-list>
      <v-list-item
        prepend-avatar="src/assets/profile-pic.png"
        title="Gabriela Mendes"
        subtitle="notmyemail@gmail.com"
      ></v-list-item>
    </v-list>

    <v-spacer></v-spacer>

    <v-btn icon>
      <v-icon
        color="grey-darken-1"
        @click.prevent="selectOption(true)"
        aria-label="Color Gallery"
        >mdi-image</v-icon
      >
    </v-btn>

    <v-btn icon>
      <v-icon
        color="grey-darken-1"
        @click.prevent="selectOption(false)"
        aria-label="Grayspace Gallery"
        >mdi-dialpad</v-icon
      >
    </v-btn>
  </v-app-bar>
</template>
