<template>
  <v-navigation-drawer
    v-model="drawer"
    style="margin-top: 3rem"
    :mini-variant="miniDrawer"
    :clipped="$vuetify.breakpoint.mdAndUp"
    fixed
    app
    width="230"
    :floating="true"
  >
    <v-list dense nav>
      <template v-for="(item, index) in items">
        <v-list-group
          v-if="item.children"
          :key="index"
          :value="false"
          :prepend-icon="item.icon"
        >
          <template v-slot:activator>
            <v-list-item-title>{{ item.title }}</v-list-item-title>
          </template>

          <v-list-item
            v-for="(child, idx) in item.children"
            :key="idx"
            link
            exact
            :to="item.link + child.link"
          >
            <v-list-item-icon>
              <v-icon>{{ child.icon }}</v-icon>
            </v-list-item-icon>

            <v-list-item-content>
              <v-list-item-title>
                {{ child.title }}
              </v-list-item-title>
            </v-list-item-content>
          </v-list-item>
        </v-list-group>
        <v-list-item v-else :key="index" link exact :to="item.link">
          <v-list-item-icon>
            <v-icon>{{ item.icon }}</v-icon>
          </v-list-item-icon>

          <v-list-item-content>
            <v-list-item-title>{{ item.title }}</v-list-item-title>
          </v-list-item-content>
        </v-list-item>
      </template>
    </v-list>
  </v-navigation-drawer>
</template>

<script lang="ts">
import Vue from 'vue';
export interface Item {
  icon: string;
  title: string;
  link: string;
  disabled: boolean;
  children?: Array<Children>;
}
export interface Children {
  icon?: string;
  title: string;
  link: string;
}
export default Vue.extend({
  name: 'SidebarLeft',
  props: {
    showDrawer: {
      type: Boolean,
      required: true,
      default: true,
    },
    miniDrawer: {
      type: Boolean,
      default: true,
    },
  },
  data: () => ({
    drawer: false,
    items: [
      {
        icon: 'mdi-home',
        title: 'Home',
        link: '/',
        disabled: false,
      },
      {
        icon: 'mdi-format-color-text',
        title: 'Anime List',
        link: '/animes',
        disabled: false,
      },
      {
        icon: 'mdi-apps',
        title: 'Release',
        disabled: false,
        link: '/releases',
        children: [
          {
            title: 'Episodes',
            link: '/posts',
          },
          {
            title: 'Notifications',
            link: '/notifications',
          },
          {
            title: 'Movie and Specials',
            link: '/movies',
          },
          {
            title: 'Batch',
            link: '/batch',
          },
          {
            title: 'Subtitles',
            link: '/subtitle',
          },
          {
            title: 'Raws',
            link: '/raws',
          },
          {
            title: 'Encoded',
            link: '/encoded',
          },
        ],
      },
      {
        icon: 'mdi-new-box',
        title: 'News',
        link: '/news',
        disabled: false,
      },
      {
        icon: 'mdi-calendar',
        title: 'Release Schedule',
        link: '/schedule',
        disabled: false,
      },
      {
        icon: 'mdi-apps',
        title: 'About Us',
        link: '/aboutUs',
        disabled: false,
      },
      {
        icon: 'mdi-comment-processing',
        title: 'Contact Us',
        link: '/contactUs',
        disabled: false,
      },
      {
        icon: 'mdi-rss',
        title: 'RSS',
        link: '/rss',
        disabled: false,
      },
    ] as Array<Item>,
  }),
  watch: {
    showDrawer() {
      this.drawer = this.showDrawer;
    },
    drawer() {
      this.$emit('changeDrawer', this.drawer);
    },
  },
});
</script>

<style scoped></style>
