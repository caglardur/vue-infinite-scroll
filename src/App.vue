<template>
  <v-app>
    <v-app-bar app color="primary" dark>
      <v-col class="mx-auto text-center">Vue2 Infinite Scroll Example</v-col>
    </v-app-bar>

    <v-main>
      <router-view />
    </v-main>
  </v-app>
</template>

<script lang="ts">
import Vue from "vue"

export default Vue.extend({
  name: "App",

  data: () => ({
    //
  })
})
</script>
