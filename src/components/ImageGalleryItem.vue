<script setup>
import { ref, computed, inject } from "vue";

const isWithColor = inject("isWithColor");

const { n } = defineProps(["n"]);

const failedImage = ref(false);
const imgUrl = computed(() =>
  !failedImage.value
    ? `https://picsum.photos/500/300?image=${n * 5 + 10}${
        isWithColor.value ? "" : "&grayscale"
      }`
    : "src/assets/notfound.png"
);

const emit = defineEmits(["copiedSuccess"]);
const copyUrl = async (url) => {
  await navigator.clipboard.writeText(url);

  emit("copiedSuccess");
};
</script>

<template>
  <v-hover v-slot="{ isHovering, props }">
    <v-card
      :style="failedImage ? 'pointer-events: none' : ''"
      :elevation="isHovering ? 12 : 2"
      v-bind="props"
      @click="
        copyUrl(
          `https://picsum.photos/500/300?image=${n * 5 + 10}${
            isWithColor ? '' : '&grayscale'
          }`
        )
      "
    >
      <v-img
        :src="imgUrl"
        :lazy-src="`https://picsum.photos/10/6?image=${n * 5 + 10}${
          isWithColor ? '' : '&grayscale'
        }`"
        v-on:error="failedImage = true"
        aspect-ratio="1"
        cover
      >
        <template v-slot:placeholder>
          <v-row class="fill-height ma-0" align="center" justify="center">
            <v-progress-circular
              indeterminate
              color="grey-lighten-5"
            ></v-progress-circular>
          </v-row>
        </template>
      </v-img>
    </v-card>
  </v-hover>
</template>
