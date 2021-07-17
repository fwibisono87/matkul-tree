<template>
  <v-app class="px-2">
    <v-main>
      <v-overlay
        :opacity="1"
        :value="loader"
        width='100%'
        color='#1e1e1e'
      >
        <v-row>
          <v-progress-circular indeterminate class='mx-auto' color='#F96b00'>
          </v-progress-circular>
        </v-row>
        <v-row>
          <span class='mx-auto'>Loading!</span>
        </v-row>
      </v-overlay>
      <v-app-bar dense fixed>
        <v-app-bar-nav-icon @click.stop='drawer = !drawer'></v-app-bar-nav-icon>
        <v-toolbar-title>
          Pacil Matkul Tree <span style='color: orange; font-weight: bold'> -BETA- </span>
        </v-toolbar-title>
      </v-app-bar>
      <v-container class='mt-12'>
        <nuxt />
      </v-container>
      <v-navigation-drawer
        v-model='drawer'
        fixed
        temporary
      >
        <v-list class='px-2 pt-2'>
          <v-list-item-title style='font-size: 125%'>Pacil Matkul Tree <span style='color: orange; font-weight: bold'> -BETA- </span></v-list-item-title>
        </v-list>
        <v-list nav dense>
          <v-list-item-group>
            <v-list-item to='/'>
              <v-list-item-icon><v-icon>mdi-home</v-icon></v-list-item-icon>
              <v-list-item-title>Home</v-list-item-title>
            </v-list-item>
            <v-list-item to='/about'>
              <v-list-item-icon><v-icon>mdi-information</v-icon></v-list-item-icon>
              <v-list-item-title>About</v-list-item-title>
            </v-list-item>
            <v-list-item to='/ilkom'>
              <v-list-item-icon><v-icon>mdi-desktop-classic</v-icon></v-list-item-icon>
              <v-list-item-title>Ilmu Komputer</v-list-item-title>
            </v-list-item>
            <v-list-item to='/si'>
              <v-list-item-icon><v-icon>mdi-clipboard-text-search-outline</v-icon></v-list-item-icon>
              <v-list-item-title>Sistem Informasi</v-list-item-title>
            </v-list-item>
          </v-list-item-group>
        </v-list>
      </v-navigation-drawer>
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
  data: () => ({
    loader: true,
    drawer: false
  }),
  created() {
    // console.log("created")
  },
  mounted(){
    // console.log("mounted")
    this.loader = false
  },
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
