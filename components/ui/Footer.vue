<template>
  <v-footer style="margin-bottom: -50px" absolute app>
    <span> &copy; 2017 - {{ new Date().getFullYear() }} </span>
    <v-btn text link exact active-class="no-active" to="/">Erai-raws</v-btn>
    <v-spacer />
    <v-btn text link exact active-class="no-active" to="/privacyPolicy">
      Privacy Policy
    </v-btn>
  </v-footer>
</template>

<style scoped>
.no-active::before {
  background-color: transparent !important;
}
</style>
