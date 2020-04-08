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
              <v-col 
              v-for="(ph_stat, index) in ph_stats"
              :key="index"
              cols="12" md="6">
                <v-card dark shaped="true">
                  <div class="d-flex flex-no-wrap justify-space-between">
                    <div>
                      <v-card-title class="display-3 font-weight-black" v-text="ph_stat.data"></v-card-title>

                      <v-card-subtitle v-text="ph_stat.title"></v-card-subtitle>
                    </div>

                    <v-avatar class="ma-3" size="125" tile>
                      <span :class="ph_stat.src"></span>
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
    ph_stats : [
      {
        title : `Today's COVID-19 Cases`,
        data: 106,
        src: "mdi mdi-account-alert display-4",
      },
      {
        title : `Total COVID-19 Cases in the Philippines`,
        data: 3870,
        src: "mdi mdi-account-group display-4",
      },
      {
        title : `Number Active Patients`,
        data: 3592,
        src: "mdi mdi-account-multiple-plus display-4",
      },
      {
        title : `Total Number of Recovered Patients`,
        data: 96,
        src: "mdi mdi-account-heart display-4",
      },

      {
        title : `Today's Deaths`,
        data: 5,
        src: "mdi mdi-shield-cross display-4",
      },
      {
        title : `Total Number of Deaths`,
        data: 182,
        src: "mdi mdi-grave-stone display-4",
      },
    ],
    ph_: {

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
