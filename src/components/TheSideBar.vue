<script setup>
const emits = defineEmits(["optionSelected"]);

const selectOption = (isColor) => {
  emits("optionSelected", isColor);
};
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
        @click="selectOption(true)"
      ></v-list-item>
      <v-list-item
        prepend-icon="mdi-dialpad"
        title="Grayspace Gallery"
        value="color"
        @click="selectOption(false)"
      ></v-list-item>
    </v-list>
  </v-navigation-drawer>
</template>
