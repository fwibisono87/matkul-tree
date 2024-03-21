<template>
  <v-container>
    <h2>Halo! Selamat datang di Pacil Matkul Tree!</h2>
    <h3>WARNING: contents of this page is long deprecated. If you would like to help update data, please email matkul-tree@franciswibisono.com</h3>
    <h3>Silahkan pilih Program Studi anda!</h3>
    <v-row>
      <v-col><v-card color='#00008B'>
        <v-list-item to='/ilkom'>
        <v-list-item-icon><v-icon>mdi-desktop-classic</v-icon></v-list-item-icon>
        <v-list-item-title>Ilmu Komputer</v-list-item-title>
        </v-list-item>
      </v-card></v-col>
      <v-col>
        <v-card color='#8B0000'>
        <v-list-item to='/si'>
          <v-list-item-icon><v-icon>mdi-clipboard-text-search-outline</v-icon></v-list-item-icon>
          <v-list-item-title>Sistem Informasi</v-list-item-title>
        </v-list-item>
      </v-card></v-col>
    </v-row>
  </v-container>
</template>

<script>
export default {
  data: () => ({
    name: "Home"
  }),
}
</script>

<style scoped>

</style>
