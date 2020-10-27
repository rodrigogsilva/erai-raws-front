<template>
  <v-app dark>
    <AppHeader @clickSideIconMenu="onClickSideIconMenu" />
    <SidebarLeft
      :showDrawer="drawer"
      :miniDrawer="mini"
      @changeDrawer="onChangeDrawer"
    />
    <v-main style="margin-top: 3rem">
      <v-img
        src="/cropped-cropped-2020.jpg"
        lazy-src="/cropped-cropped-2020.jpg"
        class="grey lighten-2"
      >
        <template v-slot:placeholder>
          <v-row class="fill-height ma-0" align="center" justify="center">
            <v-progress-circular
              indeterminate
              color="grey lighten-5"
            ></v-progress-circular>
          </v-row>
        </template>
      </v-img>

      <v-container fluid>
        <v-row justify="center">
          <v-col cols="12" sm="10" md="9">
            <v-card style="padding: 1rem">
              <transition name="fade">
                <nuxt />
              </transition>
            </v-card>
          </v-col>
          <v-col cols="12" sm="4" md="3">
            <v-card style="padding: 1rem" min-height="500">
              <SideBarRight />
            </v-card>
          </v-col>
        </v-row>
      </v-container>
      <Footer />
    </v-main>
  </v-app>
</template>

<script lang="ts">
import Vue from 'vue';
import SidebarLeft from '@/components/ui/SidebarLeft.vue';
import SideBarRight from '@/components/ui/SideBarRight.vue';
import Footer from '@/components/ui/Footer.vue';
import AppHeader from '@/components/ui/AppHeader.vue';

export default Vue.extend({
  components: {
    SideBarRight,
    Footer,
    SidebarLeft,
    AppHeader,
  },
  data() {
    return {
      drawer: false,
      mini: false,
    };
  },
  methods: {
    onClickSideIconMenu() {
      if (this.$vuetify.breakpoint.mdAndUp) {
        this.mini = !this.mini;
      } else {
        this.mini = false;
        this.drawer = !this.drawer;
      }
    },
    onChangeDrawer(value: boolean) {
      this.drawer = value;
    },
  },
  head() {
    return {
      titleTemplate: '%s | Erai Raws',
      meta: [
        {
          hid: 'description',
          name: 'description',
          content: 'Great animes, there are subs too...',
        },
      ],
    };
  },
});
</script>

<style scoped></style>
