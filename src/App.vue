<template>
  <v-app>
    <v-app-bar app color="primary" dark>
      <v-col sm="12" md="6" lg="4" class="d-flex align-center ma-0 pa-0 mx-auto">
        <v-row align="center">
          <v-col>Vue2 Infinite Scroll Example </v-col>
          <v-spacer></v-spacer>
          <v-col cols="auto">
            <v-btn icon href="https://github.com/caglardur/vue-infinite-scroll" target="_blank"><v-icon>mdi-github</v-icon></v-btn>
          </v-col>
        </v-row>
      </v-col>
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
