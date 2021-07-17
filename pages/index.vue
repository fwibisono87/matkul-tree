<template>
  <v-container>
    <span>Halo! Selamat datang di Pacil Matkul Tree!</span>
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
          <v-list-item-title>Sistem Informasi (Partial Impl.)</v-list-item-title>
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
