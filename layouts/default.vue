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
      <v-app-bar dense>
        Pacil Matkul Tree <span style='color: orange; font-weight: bold'> -BETA- </span> Ilmu Komputer Wajib
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
      <v-snackbar
        :value='true'
        :multi-line="multiLine"
        :timeout='10000'
      >
        Halo! Situs ini masih dalam perkembangan!<br /> Saat ini, baru MK Wajib Ilkom Terimplementasi!<br />Mohon berikan feedback ke francis.wibisono@ui.ac.id
        <template v-slot:action='{ attrs }'>
          <v-btn
            color="orange"
            text
            v-bind="attrs"
            @click="snackbar = false"
          >
            Close
          </v-btn>
        </template>
      </v-snackbar>
    </v-main>
  </v-app>
</template>

<script>
export default {
  name: 'default',
  data: () => ({
    loader: true
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
