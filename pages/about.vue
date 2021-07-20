<template>
  <v-container>
    <v-card>
      <v-card-title>
        <h2>
          Tentang
        </h2>
      </v-card-title>
      <v-card-text>
        <p>Pacil Matkul Tree merupakan sebuah website yang diperuntukkan untuk membantu mahasiswa Fakultas Ilmu Komputer, Universitas Indonesia memilih mata kuliah yang dapat diambil sesuai prerekuisit yang ada.</p>
        <p>Saat ini, web app ini masih ada dalam pengembangan, dan baru mengimplementasikan mata kuliah wajib Program Studi Ilmu Komputer dan Program Studi Sistem Informasi.</p>
        <p>Seluruh kritik dan saran dapat dikirimkan ke <a href='mailto:francis.wibisono@ui.ac.id' target='_blank'>francis.wibisono@ui.ac.id</a> </p>
        <p>Repositori kode website ini dapat diakses di <a href='https://github.com/fwibisono87/matkul-tree/' target='_blank'>github.com/fwibisono87/matkul-tree/</a> </p>
      </v-card-text>
      <v-card-subtitle>
        <h4>
          Sumber
        </h4>
      </v-card-subtitle>
      <v-card-text>
        <ul>
          <li>
            <a href='https://scele.cs.ui.ac.id/pluginfile.php/1279/block_html/content/Kurikulum%20Sarjana%202016.pdf'>
              Buku Kurikulum Sarjana 2016
            </a>
          </li>
          <li>
            <a href='https://scele.cs.ui.ac.id/pluginfile.php/1279/block_html/content/HighlightKurikulumSI_Reg-2020-v1.1-2feb21.pdf' target='_blank'>
              Highlight Perubahan pada Kurikulum Program Studi
              Sarjana Sistem Informasi 2020 dan Pelaksanaannya
              Selama Masa Transisi
            </a>
          </li>
          <li>
            <a href='https://scele.cs.ui.ac.id/pluginfile.php/1279/block_html/content/Highight%20Transisi%20Kurikulum%202020%20PSIK-publish.pdf' target='_blank'>
              Highlight Perubahan pada Kurikulum Program Studi
              Sarjana Ilmu Komputer 2020 dan Pelaksanaannya
              Selama Masa Transisi
            </a>
          </li>
        </ul>
      </v-card-text>
      <v-card-subtitle>
        <h4>
          Kontributor
        </h4>
      </v-card-subtitle>
      <v-card-text>
        <v-container>
          <v-row>
            <v-col>
              <span>Code: <a href='http://www.franciswibisono.com'>Francis Wibisono</a></span>
            </v-col>
            <v-col>Ilkom Data Entry: Francis W</v-col>
            <v-col>SI Data Entry: Kevina Felie A</v-col>
          </v-row>
          <v-row><v-col cols='12' style='text-align: center!important'><h4>Beta Testers</h4></v-col></v-row>
          <v-row>
            <v-col><span>Mustafa Z.</span></v-col>
            <v-col><span>Eyota W.</span></v-col>
            <v-col><span>Erasto A.</span></v-col>
            <v-col><span>Hasiana E.</span></v-col>
            <v-col><span>Gabriel E.</span></v-col>
            <v-col><span>Nabila K.</span></v-col>
            <v-col><span>Wening D.</span></v-col>
            <v-col><span>Abdillah E.</span></v-col>
            <v-col><span>Amanda A.</span></v-col>
            <v-col><span>Abdurrafi</span></v-col>
          </v-row>
          <v-row>
            <v-col><span>Fariz E.</span></v-col>
            <v-col><span>Marcia N.</span></v-col>
            <v-col><span>Anggardha F.</span></v-col>
            <v-col><span>Muhammad Z.</span></v-col>
            <v-col><span>Teofanus G.</span></v-col>
            <v-col><span>Yudhistira G.</span></v-col>
            <v-col><span>Cynthia P.</span></v-col>
            <v-col><span>I Gede A.</span></v-col>
            <v-col><span>Josephine C.</span></v-col>
            <v-col><span>Arsita R.</span></v-col>
          </v-row>
        </v-container>
      </v-card-text>
    </v-card>
  </v-container>
</template>

<script>
export default {
  name: 'about',
}
</script>

<style scoped>
  a{
    color: white;
  }
</style>
