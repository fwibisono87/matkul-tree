<template>
  <div>
    <v-container>
      <v-row dense>
        <v-col>
          <h1>Ilmu Komputer</h1>
        </v-col>
        <v-col>
          <v-row dense>
            <v-col>
              <v-list-item dense>
                <v-list-item-icon>
                  <v-icon color='#1e1e1e'>mdi-circle</v-icon>
                </v-list-item-icon>
                <v-list-item-subtitle>Belum Bisa Diambil</v-list-item-subtitle>
              </v-list-item>
            </v-col>
            <v-col>
              <v-list-item dense>
                <v-list-item-icon>
                  <v-icon color='#006400'>mdi-circle</v-icon>
                </v-list-item-icon>
                <v-list-item-subtitle>Sudah Diambil</v-list-item-subtitle>
              </v-list-item>
            </v-col>
            <v-col>
              <v-list-item dense>
                <v-list-item-icon>
                  <v-icon color='#d46b08'>mdi-circle</v-icon>
                </v-list-item-icon>
                <v-list-item-subtitle>Bisa Diambil</v-list-item-subtitle>
              </v-list-item>
            </v-col>
          </v-row>
        </v-col>
      </v-row>
    </v-container>
    <v-expansion-panels multiple>
      <v-expansion-panel
        v-for='semester in data1'
        :key='semester'
      >
        <v-expansion-panel-header>
          <h2>
            {{ semester.name }}
          </h2>
        </v-expansion-panel-header>
        <v-expansion-panel-content>
          <v-row dense>
            <v-col
              v-for='matkul in semester.matkuls'
              :key='matkul'
              cols='12'
              sm='6'
              md='4'
              lg='3'
            >
              <v-card
                v-if='matkul.selectable || dependencyDriver(matkul.dependency)'
                :color="matkul.selected===true ? '#006400' : matkul.selectable || dependencyDriver(matkul.dependency)===true ? '#d46b08' : '#1e1e1e'"
                height='100%'
                min-height='150px'
              >
                <v-card-title>
                  {{ matkul.stitle }}
                </v-card-title>
                <v-card-subtitle>
                  {{matkul.ltitle}}
                </v-card-subtitle>
                <v-card-text v-if='joinDependency(matkul.dependency)===""'>
                  Tidak memiliki prerekuisit
                </v-card-text>
                <v-card-text v-else>
                  <span>Prerekuisit: </span>
                  {{joinDependency(matkul.dependency)}}
                </v-card-text>
                <v-divider></v-divider>
                <v-card-actions>
                  <v-dialog
                    v-model='matkul.details'
                    max-width='700px'
                  >
                    <template #activator="{ on, attrs }">
                      <v-btn
                        text
                        v-bind='attrs'
                        v-on='on'
                      >
                        Detail
                      </v-btn>
                    </template>
                    <v-card>
                      <v-card-title>
                        {{matkul.stitle}}
                      </v-card-title>
                      <v-card-text>
                        {{matkul.description}}
                      </v-card-text>
                      <v-divider></v-divider>
                      <v-card-actions>
                        <v-btn text @click='matkul.details = false'>
                          Tutup
                        </v-btn>
                      </v-card-actions>
                    </v-card>
                  </v-dialog>
                  <v-btn
                    v-if='!matkul.selected'
                    text
                    @click='matkul.selected = !matkul.selected'
                  >
                    Ambil
                  </v-btn>
                  <v-btn
                    v-else
                    text
                    @click='matkul.selected = !matkul.selected'
                  >
                    Lepas
                  </v-btn>
                </v-card-actions>
              </v-card>
              <v-card
                v-else
                height='100%'
                min-height='150px'
                style='border-style: solid!important; border-color: rgba(255, 255, 255, 0.12);!important;'
              >
                <v-card-title>
                  {{ matkul.stitle }}
                </v-card-title>
                <v-card-subtitle>
                  {{matkul.ltitle}}
                </v-card-subtitle>
                <v-card-text v-if='joinDependency(matkul.dependency)===""'>
                  Tidak memiliki prerekuisit
                </v-card-text>
                <v-card-text v-else>
                  <span>Prerekuisit: </span>
                  {{joinDependency(matkul.dependency)}}
                </v-card-text>
                <v-divider></v-divider>
                <v-card-actions>
                  <v-dialog
                    v-model='matkul.details'
                    max-width='700px'
                  >
                    <template #activator="{ on, attrs }">
                      <v-btn
                        text
                        v-bind='attrs'
                        v-on='on'
                      >
                        Detail
                      </v-btn>
                    </template>
                    <v-card>
                      <v-card-title>
                        {{matkul.stitle}}
                      </v-card-title>
                      <v-card-text>
                        {{matkul.description}}
                      </v-card-text>
                      <v-divider></v-divider>
                      <v-card-actions>
                        <v-btn text @click='matkul.details = false'>
                          Tutup
                        </v-btn>
                      </v-card-actions>
                    </v-card>
                  </v-dialog>
                </v-card-actions>
              </v-card>
            </v-col>
          </v-row>
        </v-expansion-panel-content>
      </v-expansion-panel>
    </v-expansion-panels>
  </div>
</template>

<script>
export default {
  name: 'Index',
  data: () => ({
    data1: [],
  }),
  mounted() {
    this.data1 = JSON.parse(JSON.stringify(require('assets/ilkom.json')))
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
