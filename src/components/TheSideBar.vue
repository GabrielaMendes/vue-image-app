<template>
  <v-navigation-drawer :width="280" expand-on-hover rail>
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
      ></v-list-item>
      <v-list-item
        prepend-icon="mdi-dialpad"
        title="Grayspace Gallery"
        value="grayspace"
      ></v-list-item>
    </v-list>
  </v-navigation-drawer>
</template>
