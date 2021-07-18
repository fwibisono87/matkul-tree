<template>
  <div>
    <h1>Sistem Informasi</h1>
    <div>
      <v-container>
        <span>Tekan card mata kuliah untuk menandai sebagai 'sudah diambil!'</span>
        <v-row dense>
          <v-col cols='4'>
            <!--suppress HtmlDeprecatedAttribute -->
            <v-card color='#1e1e1e' min-height='100%' align='center'>Belum bisa diambil</v-card>
          </v-col>
          <v-col cols='4'>
            <!--suppress HtmlDeprecatedAttribute -->
            <v-card color='#006400' min-height='100%' align='center'>Sudah diambil</v-card>
          </v-col>
          <v-col cols='4'>
            <!--suppress HtmlDeprecatedAttribute -->
            <v-card color='#d46b08' min-height='100%' align='center'>Bisa diambil</v-card>
          </v-col>
        </v-row>
      </v-container>
    </div>
    <v-container v-for='semester in data1' :key='semester'>
      <h2>{{ semester.name }}</h2>
      <v-row dense>
        <v-col
          v-for='matkul in semester.matkuls'
          :key='matkul'
          cols='12'
          sm='6'
          md='4'
          lg='3'
          max-width='50%'
        >
          <v-card
            v-if='matkul.selectable || dependencyDriver(matkul.dependency)===true'
            :color="matkul.selected===true ? '#006400' : matkul.selectable || dependencyDriver(matkul.dependency)===true ? '#d46b08' : '#1e1e1e'"
            height='100%'
            min-height='150px'
            @click='matkul.selected = !matkul.selected'
          >
            <v-card-title>{{matkul.stitle}}</v-card-title>
            <v-card-subtitle>{{matkul.ltitle}}</v-card-subtitle>
            <v-card-text>
              {{matkul.description}} <br />
            </v-card-text>
            <v-card-subtitle v-if='joinDependency(matkul.dependency) !== ""'>
              <span>Prerekuisit:</span>
              {{joinDependency(matkul.dependency)}}
            </v-card-subtitle>
          </v-card>
          <v-card
            v-else
            height='100%'
            min-height='150px'
          >
            <v-card-title>{{matkul.stitle}}</v-card-title>
            <v-card-subtitle>{{matkul.ltitle}}</v-card-subtitle>
            <v-card-text>
              {{matkul.description}} <br />
            </v-card-text>
            <v-card-subtitle v-if='joinDependency(matkul.dependency) !== ""'>
              <span>Prerekuisit:</span>
              {{joinDependency(matkul.dependency)}}
            </v-card-subtitle>
          </v-card>
        </v-col>
      </v-row>
    </v-container>
  </div>
</template>

<script>
export default {
  name: 'index',
  data: () => ({
    data1: [],
  }),
  mounted() {
    this.data1 = JSON.parse(JSON.stringify(require('assets/si.json')))
    // await console.log(this.dependencyDriver(['MatDas 1', 'MatDas 2']))
  },
  methods: {
    joinDependency(dependencyList){
      return dependencyList.join(', ')
    },
    dependencyDriver(dependencyList){
      // console.log("checking!")
      if(dependencyList===[]){
        // console.log("empty dependency!")
        return true
      }
      let result = false
      for(let i = 0; i<dependencyList.length; i++){
        result = this.checkDependency(dependencyList[i])
        if(result===false){return false}
        else continue
      }
      return result
    },
    checkDependency(value) {
      const list = this.data1
      // console.log(list)
      for(let SemesterCount = 0; SemesterCount<list.length; SemesterCount++){
        // console.log(list[SemesterCount])
        const thisSemester = list[SemesterCount]
        const thisSemesterMatkuls = thisSemester.matkuls
        // console.log(thisSemesterMatkuls)
        for (let MatkulCount = 0; MatkulCount<thisSemesterMatkuls.length; MatkulCount++){
          if(thisSemesterMatkuls[MatkulCount].stitle === value){
            if(thisSemesterMatkuls[MatkulCount].selected){
              return true
            }
            else return false
          }
        }
      }
    }
  }
}
</script>

<style scoped>

</style>
