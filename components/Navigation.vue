<template>
  <v-app-bar app>
    <nuxt-link exact aria-label="Go to home" to="/">
      <v-img
        class="mx-2"
        :src="$icon(64)"
        max-height="40"
        max-width="40"
        contain
        alt="Website Logo"
      />
    </nuxt-link>
    <v-toolbar-title @click="$router.push('/')">
      Manoah's Portfolio
    </v-toolbar-title>
    <v-spacer />
    <v-toolbar-items class="hidden-sm-and-down">
      <v-btn v-for="item in pages" :key="item.title" :to="item.to" nuxt exact>
        <v-icon left>{{ item.icon }}</v-icon>
        {{ item.title }}
      </v-btn>
    </v-toolbar-items>
    <v-spacer />
    <v-toolbar-items class="hidden-xs-only">
      <v-btn
        v-for="link in links"
        :key="link.title"
        icon
        :aria-label="link.title"
        :href="link.to"
        target="_blank"
      >
        <v-icon>{{ link.icon }}</v-icon>
      </v-btn>
      <v-btn icon aria-label="Toggle dark mode" @click="toggleDarkMode">
        <v-icon>{{ mdiBrightness6 }}</v-icon>
      </v-btn>
    </v-toolbar-items>
  </v-app-bar>
</template>
<script>
import { mdiBrightness6 } from '@mdi/js'
export default {
  props: {
    pages: {
      type: Array,
      required: true,
    },
    links: {
      type: Array,
      default: () => {
        return []
      },
    },
  },
  data() {
    return {
      mdiBrightness6,
    }
  },
  methods: {
    toggleDarkMode() {
      this.$vuetify.theme.dark = !this.$vuetify.theme.dark
    },
  },
}
</script>
<style lang="scss" scoped>
.v-toolbar__title {
  cursor: pointer;
  min-width: 183px;
}
</style>
