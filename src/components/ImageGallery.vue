<script setup>
import { onMounted } from "vue";
import ImageGalleryItem from "./ImageGalleryItem.vue";
import { ref } from "vue";

const showAlert = ref(false);

let timer = null;
const onCopiedSuccess = () => {
  clearTimeout(timer);
  showAlert.value = true;

  timer = setTimeout(() => {
    showAlert.value = false;
  }, 5000);
};

const target = ref(null);
const disabled = ref(false);

onMounted(() => {
  target.value = "#alert";
});
</script>

<template>
  <v-card class="mx-5 my-2 pa-3">
    <v-row>
      <v-col v-for="n in 200" :key="n" cols="4" sm="3" md="2" lg="1">
        <ImageGalleryItem :n="n" @copied-success="onCopiedSuccess" />
      </v-col>
    </v-row>
  </v-card>

  <!-- Coppied Alert -->
  <teleport :to="target" :disabled="!target || disabled">
    <transition name="slide">
      <v-alert
        v-model="showAlert"
        closable
        @click:close="showAlert = false"
        text="Url copied to clipboard!"
        type="success"
        variant="tonal"
        style="background-color: rgba(255, 255, 255, 0.95)"
      ></v-alert>
    </transition>
  </teleport>
</template>

<style scoped>
.slide-enter-from,
.slide-leave-to {
  transform: translateY(-100%);
}

.slide-enter-active,
.slide-leave-active {
  transition: transform 400ms ease-out;
}
</style>
