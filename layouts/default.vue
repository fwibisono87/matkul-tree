<template>
  <v-app class="px-2">
    <v-main>
      <v-app-bar dense>
        Pacil Matkul Tree
      </v-app-bar>
      <v-container min-height='100%'>
        <nuxt />
      </v-container>
      <v-btn
        fab
        dark
        fixed
        bottom
        right
        @click="toTop"
      >
        <v-icon>mdi-arrow-up</v-icon>
      </v-btn>
    </v-main>
  </v-app>
</template>

<script>
export default {
  name: 'default',
  methods: {
    onScroll (e) {
      if (typeof window === 'undefined') return
      const top = window.pageYOffset ||   e.target.scrollTop || 0
      this.fab = top > 20
    },
    toTop () {
      this.$vuetify.goTo(0)
    }
  }
}
</script>

<style scoped>

</style>
