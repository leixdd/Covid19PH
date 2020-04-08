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
              <v-col v-for="(ph_stat, index) in ph_stats" :key="index" cols="12" md="6">
                <v-card dark :shaped="true">
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
import axios from "axios";

export default {
  props: {
    source: String
  },

  data: () => ({
    drawer: null,
    ph_stats: []
  }),

  methods: {
    async loadSource() {
      this.ph_stats = await axios
        .get("https://corona.lmao.ninja/countries/ph")
        .catch(err => console.log(err))
        .then(data => {
          return [
            {
              title: `Today's COVID-19 Cases`,
              data: data.data.todayCases,
              src: "mdi mdi-account-alert display-4"
            },
            {
              title: `Total COVID-19 Cases in the Philippines`,
              data: data.data.cases,
              src: "mdi mdi-account-group display-4"
            },
            {
              title: `Number Active Patients`,
              data: data.data.active,
              src: "mdi mdi-account-multiple-plus display-4"
            },
            {
              title: `Total Number of Recovered Patients`,
              data: data.data.recovered,
              src: "mdi mdi-account-heart display-4"
            },

            {
              title: `Today's Deaths`,
              data: data.data.todayDeaths,
              src: "mdi mdi-shield-cross display-4"
            },
            {
              title: `Total Number of Deaths`,
              data: data.data.deaths,
              src: "mdi mdi-grave-stone display-4"
            }
          ];
        });
    }
  },

  created() {
    this.$vuetify.theme.dark = true;
  },

  mounted() {
    this.loadSource();
  }
};
</script>
