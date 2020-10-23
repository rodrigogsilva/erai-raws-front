<template>
  <v-app-bar
    fixed
    dense
    class="red--text"
    :clipped-left="$vuetify.breakpoint.mdAndUp"
  >
    <v-app-bar-nav-icon @click="$emit('clickSideIconMenu')" />
    <v-toolbar-title v-text="title" />
  </v-app-bar>
</template>

<script lang="ts">
import Vue from 'vue';

export default Vue.extend({
  name: 'AppHeader',
  data: () => ({
    title: 'Erai Raws',
  }),
});
</script>

<style scoped></style>
