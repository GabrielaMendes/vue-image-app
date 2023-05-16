<script setup>
const { isWithColor } = defineProps({
  isWithColor: {
    required: true,
    type: String,
  },
});

const copyUrl = async (url) => {
  await navigator.clipboard.writeText(url);
};
</script>

<template>
  <v-card class="mx-5 my-2 pa-3">
    <v-row>
      <v-col v-for="n in 200" :key="n" cols="4" sm="3" md="2" lg="1">
        <v-hover v-slot="{ isHovering, props }">
          <v-card
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
              :src="`https://picsum.photos/500/300?image=${n * 5 + 10}${
                isWithColor ? '' : '&grayscale'
              }`"
              :lazy-src="`https://picsum.photos/10/6?image=${n * 5 + 10}${
                isWithColor ? '' : '&grayscale'
              }`"
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
      </v-col>
    </v-row>
  </v-card>
</template>
