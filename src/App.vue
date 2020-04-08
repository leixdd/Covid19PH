<template>
  <v-app id="inspire">
    <v-app-bar app clipped-left>
      <v-toolbar-title>Covid19 PH</v-toolbar-title>
    </v-app-bar>

    <v-content>
      <v-container fluid>
        <v-row>
          <v-col cols="12" md="8">
            <v-row>
              <v-col cols="12" md="6">
                <v-card :color="item.color" dark>
                  <div class="d-flex flex-no-wrap justify-space-between">
                    <div>
                      <v-card-title class="headline" v-text="item.title"></v-card-title>

                      <v-card-subtitle v-text="item.artist"></v-card-subtitle>
                    </div>

                    <v-avatar class="ma-3" size="125" tile>
                      <v-img :src="item.src"></v-img>
                    </v-avatar>
                  </div>
                </v-card>
              </v-col>

              <v-col cols="12" md="6">
                <v-card dark>
                  <div class="d-flex flex-no-wrap justify-space-between">
                    <div>
                      <v-card-title class="headline" v-text="item.title"></v-card-title>

                      <v-card-subtitle v-text="item.artist"></v-card-subtitle>
                    </div>

                    <v-avatar class="ma-3" size="125" tile>
                      <v-img :src="item.src"></v-img>
                    </v-avatar>
                  </div>
                </v-card>
              </v-col>
            </v-row>
          </v-col>

          <v-col cols="12" md="4">test</v-col>
        </v-row>
      </v-container>
    </v-content>

    <v-footer app>
      <span>&copy; 2019</span>
    </v-footer>
  </v-app>
</template>

<script>
// import axios from "axios";

export default {
  props: {
    source: String
  },

  data: () => ({
    drawer: null,
    ph_stats: {
      updated: 1586367093695,
      cases: 3870,
      todayCases: 106,
      deaths: 182,
      todayDeaths: 5,
      recovered: 96,
      active: 3592,
      critical: 1,
      casesPerOneMillion: 35,
      deathsPerOneMillion: 2,
      tests: 24500,
      testsPerOneMillion: 224
    },
    item: {
      src: "https://cdn.vuetifyjs.com/images/cards/foster.jpg",
      title: "Supermodel",
      artist: "Foster the People"
    }
  }),

  methods: {
    async loadSource() {
      // this.ph_stats = await axios.get().catch(err => console.log(err)).then(data => { return data;})
    }
  },

  created() {
    this.$vuetify.theme.dark = true;
  }
};
</script>
