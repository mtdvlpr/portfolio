<template>
  <v-row justify="center" align="center" :class="{ small: !preview }">
    <v-col v-for="(card, i) in cards" :key="i" md="6" lg="5">
      <v-hover v-slot="{ hover }">
        <v-card :href="card.to" class="pa-2 mb-2 mx-1">
          <v-img
            :src="
              require(`@/assets/img/${
                card.image ? card.image : 'white.webp'
              }?vuetify-preload`)
            "
            class="white--text"
            :class="hover ? 'align-start' : 'align-end'"
            gradient="to bottom, rgba(0,0,0,.1), rgba(0,0,0,.5)"
            height="200px"
            alt=""
          >
            <v-scale-transition>
              <div
                v-if="hover"
                class="d-flex justify-center align-center text-h4 transition-fast-in-fast-out white--text"
                style="height: 200px; background-color: rgba(0, 0, 0, 60%)"
              >
                Open project
              </div>
            </v-scale-transition>
            <v-card-title v-if="!hover">
              {{ card.title }}
            </v-card-title>
            <v-card-subtitle v-if="!hover && card.subtitle">
              {{ card.subtitle }}
            </v-card-subtitle>
          </v-img>
        </v-card>
      </v-hover>
    </v-col>
    <v-col v-if="preview" cols="12" class="text-center">
      <v-btn color="primary" to="/projects" nuxt>See all projects</v-btn>
    </v-col>
  </v-row>
</template>
<script>
export default {
  props: {
    cards: {
      type: Array,
      required: true,
    },
    preview: {
      type: Boolean,
      default: false,
    },
  },
}
</script>
<style lang="scss" scoped>
.v-card {
  cursor: pointer;
}
.small {
  width: 80%;
  margin: 0 auto;
}
</style>
