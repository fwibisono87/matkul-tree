<template>
  <div>
    <v-container v-for='semester in data1' :key='semester'>
      <h4>{{ semester.name }}</h4>
      <v-row dense>
        <v-col
          v-for='matkul in semester.matkuls'
          :key='matkul'
          max-width='50%'
        >
          <v-card
            @click='matkul.selected = !matkul.selected'
            :color="matkul.selected==true ? '#006400' : dependencyDriver(matkul.dependency)===true ? '#F96b00': '#1e1e1e'"
            height='100%'
            min-height='300px'
          >
            <v-card-title>{{matkul.stitle}}</v-card-title>
            <v-card-subtitle>{{matkul.ltitle}}</v-card-subtitle>
            <v-card-text>{{matkul.description}}</v-card-text>
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
  async mounted() {
    this.data1 = JSON.parse(JSON.stringify(require('~/assets/matkul.json')))
    await console.log(this.dependencyDriver(['MatDas 1', 'MatDas 2']))
  },
  methods: {
    dependencyDriver(dependencyList){
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
      console.log(list)
      for(let SemesterCount = 0; SemesterCount<list.length; SemesterCount++){
        console.log(list[SemesterCount])
        const thisSemester = list[SemesterCount]
        const thisSemesterMatkuls = thisSemester.matkuls
        console.log(thisSemesterMatkuls)
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
