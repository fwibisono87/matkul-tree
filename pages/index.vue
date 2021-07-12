<template>
  <v-container>
    <h4>Semester 1</h4>
    <v-row dense>
      <v-col>
        <v-card class='card pa-1' height = '100%' max-height='400px' min-width='30%' @click='matkul.mpkta = !matkul.mpkta' :color="matkul.mpkta==true ? '#006400' : '#1e1e1e'">
          <v-card-title>MPKT-A</v-card-title>
          <v-card-subtitle>Mata Kuliah Pengembangan Kepribadian Terintegrasi - A</v-card-subtitle>
          <v-card-text>PPKn but more retarded</v-card-text>
        </v-card>
      </v-col>
      <v-col>
        <v-card class='card pa-1' height = '100%' max-height='400px' min-width='30%' @click='matkul.mpktb = !matkul.mpktb' :color="matkul.mpktb==true ? '#006400' : '#1e1e1e'">
          <v-card-title>MPKT-B</v-card-title>
          <v-card-subtitle>Mata Kuliah Pengembangan Kepribadian Terintegrasi - B</v-card-subtitle>
          <v-card-text>PPKn but more retarded, with t e c h n o l o g y</v-card-text>
        </v-card>
      </v-col>
      <v-col>
        <v-card class='card pa-1' height = '100%' max-height='400px' min-width='30%' @click='matkul.agama = !matkul.agama' :color="matkul.agama==true ? '#006400' : '#1e1e1e'">
          <v-card-title>MPK Agama</v-card-title>
          <v-card-subtitle>Mata Kuliah Agama *</v-card-subtitle>
          <v-card-text>... agama ...</v-card-text>
        </v-card>
      </v-col>
      <v-col>
        <v-card class='card pa-1' height = '100%' max-height='400px' min-width='30%' @click='matkul.inggris = !matkul.inggris' :color="matkul.inggris==true ? '#006400' : '#1e1e1e'">
          <v-card-title>MPK B.Ing</v-card-title>
          <v-card-subtitle>Mata Kuliah Bahasa Inggris</v-card-subtitle>
          <v-card-text>Free 3 sks lol</v-card-text>
        </v-card>
      </v-col>
      <v-col>
        <v-card class='card pa-1' height = '100%' max-height='400px' min-width='30%' @click='matkul.olahragaseni = !matkul.olahragaseni' :color="matkul.olahragaseni==true ? '#006400' : '#1e1e1e'">
          <v-card-title>MPKO/S</v-card-title>
          <v-card-subtitle>Mata Kuliah Olahraga/Seni</v-card-subtitle>
          <v-card-text>recreation time</v-card-text>
        </v-card>
      </v-col>
    </v-row>
  </v-container>
</template>

<script>
export default {
  name: 'index',
  data() {
  return {
      matkul :{
        'mpkta': false,
        'mpktb': false,
        'agama': false,
        'inggris': false,
        'olahragaseni': false,
      }
    };
  }
}
</script>

<style scoped>

</style>
