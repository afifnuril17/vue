<template>
  <div class="container">
    <div class="text-center">
      <div v-if="!isLoading">
        <v-alert
          v-if="getDataEtnis"
          type="success"
          transition="scale-transition"
          dismissible
        >
          Berhasil Ambil data Etnis
        </v-alert>
        <v-alert
          v-else
          type="success"
          transition="scale-transition"
          dismissible
        >
          Gagal Ambil data Etnis
        </v-alert>
        <v-alert
          v-if="getDataAgama"
          type="success"
          transition="scale-transition"
          dismissible
        >
          Berhasil Ambil data Agama
        </v-alert>
        <v-alert v-else type="error" transition="scale-transition" dismissible>
          Gagal Ambil data Agama
        </v-alert>
      </div>
      <h1>Chart Suku Etnis TLD20</h1>
      <div class="dropdown">
        <span v-if="tahunTF == null">Tahun TF</span>
        <span v-else>{{ tahunTF }}</span>
        <div class="dropdown-content">
          <v-card
            elevation="8"
            class="my-2"
            @click="
              {
                {
                  initiateDataFilter(2021);
                }
              }
            "
            >2021</v-card
          >
          <v-card
            elevation="8"
            class="my-2"
            @click="
              {
                {
                  initiateDataFilter(2022);
                }
              }
            "
            >2022</v-card
          >
          <v-card
            elevation="8"
            class="my-2"
            @click="
              {
                {
                  initiateDataFilter(2020);
                }
              }
            "
            >2020</v-card
          >
        </div>
      </div>
      <v-card width="90%" class="mx-auto pa-5 align-center ma-5">
        <apexchart
          v-if="!isLoading"
          width="100%"
          type="bar"
          :options="options"
          :series="series"
        ></apexchart>
      </v-card>
    </div>
    <v-row>
      <v-col sm="12" md="6" lg="6">
        <v-card width="100%" height="100%" class="align-center py-5">
          <apexchart
            v-if="!isLoading"
            type="pie"
            width="50%"
            :options="chartOptions"
            :series="seriespie"
          ></apexchart>
        </v-card>
      </v-col>
      <v-col sm="12" md="6" lg="6">
        <v-card width="100%" class="align-center py-5">
          <apexchart
            type="line"
            height="100%"
            :options="chartOptionsLine"
            :series="seriesLine"
          ></apexchart>
        </v-card>
      </v-col>
    </v-row>
  </div>
</template>
<script lang="ts">
import Vue from "vue";
import VueApexCharts from "vue-apexcharts";
import axios from "axios";

export default Vue.extend({
  components: {
    apexchart: VueApexCharts,
  },
  data() {
    return {
      isLoading: true,
      options: null,
      series: null,
      token: null,
      seriespie: null,
      chartOptions: null,
      tahunTF: 2020,
      getDataEtnis: null,
      getDataAgama: null,
      seriesLine: null,
      chartOptionsLine: null,
    };
  },
  mounted() {
    this.initiateData();
  },
  methods: {
    async initiateData() {
      this.isLoading = true;
      this.getDataEtnis = null;
      this.getDataAgama = null;
      if (await this.postPost()) {
        await this.getDataBarChart();
        await this.getDataLineChart();
        await this.getDataPieChart();
      }
      this.isLoading = false;
    },
    async initiateDataFilter(value) {
      this.isLoading = true;
      this.tahunTF = value;
      this.getDataEtnis = null;
      this.getDataAgama = null;
      await this.getDataBarChart();
      await this.getDataLineChart();
      await this.getDataPieChart();
      this.isLoading = false;
    },
    async postPost() {
      try {
        var response = await axios.post(
          `https://backend-teladan.gamifindo.com/api/auth/login?key=superadmin@gmail.com&password=bmmrhdb2021!`
        );
        if (response.data.code == 200) {
          this.token = response.data.token;
          return true;
        }
      } catch (e) {
        this.errors.push(e);
        return false;
      }
    },
    async getDataBarChart() {
      try {
        console.log(this.tahunTF);

        var response = await axios.get(
          `https://backend-teladan.gamifindo.com/api/infografis/get-scholar?kategori=etnis&tahun_tf=${this.tahunTF}`,
          {
            headers: {
              Authorization: `Bearer ${this.token}`,
            },
          }
        );
        if (response.data.code == 200) {
          this.options = {
            chart: {
              id: "vuechart-example",
            },
            xaxis: {
              categories: Object.keys(response.data.data),
            },
          };
          this.series = [
            {
              name: "series-1",
              data: Object.values(response.data.data),
            },
          ];
          this.getDataEtnis = true;
        } else {
          this.getDataEtnis = false;
        }
      } catch (e) {
        this.getDataEtnis = false;
        this.errors.push(e);
      }
    },
    async getDataPieChart() {
      try {
        var response = await axios.get(
          `https://backend-teladan.gamifindo.com/api/infografis/get-scholar?kategori=agama&tahun_tf=${this.tahunTF}`,
          {
            headers: {
              Authorization: `Bearer ${this.token}`,
            },
          }
        );
        if (response.data.code == 200) {
          this.seriespie = Object.values(response.data.data);
          this.chartOptions = {
            chart: {
              width: 380,
              type: "pie",
            },
            labels: Object.keys(response.data.data),
            responsive: [
              {
                breakpoint: 480,
                options: {
                  chart: {
                    width: 200,
                  },
                  legend: {
                    position: "bottom",
                  },
                },
              },
            ],
          };
          this.getDataAgama = true;
        } else {
          this.getDataAgama = false;
        }
      } catch (e) {
        this.getDataAgama = false;
        this.errors.push(e);
      }
      this.isLoading = false;
    },
    async getDataLineChart() {
      try {
        var response = await axios.get(
          `https://backend-teladan.gamifindo.com/api/infografis/get-scholar?kategori=jenis_kelamin&tahun_tf=${this.tahunTF}`,
          {
            headers: {
              Authorization: `Bearer ${this.token}`,
            },
          }
        );
        if (response.data.code == 200) {
          this.seriesLine = [
            {
              name: "Jenis Kelamin",
              data: Object.values(response.data.data),
            },
          ];
          this.chartOptionsLine = {
            chart: {
              height: 350,
              type: "line",
              zoom: {
                enabled: false,
              },
            },
            dataLabels: {
              enabled: false,
            },
            stroke: {
              curve: "straight",
            },
            title: {
              text: "Jumlah peserta berdasarkan Jenis Kelamin",
              align: "Center",
            },
            grid: {
              row: {
                colors: ["#f3f3f3", "transparent"], // takes an array which will be repeated on columns
                opacity: 0.5,
              },
            },
            xaxis: {
              categories: Object.keys(response.data.data),
            },
          };
        }
      } catch (e) {
        this.errors.push(e);
      }
      this.isLoading = false;
    },
  },
});
</script>

<style scoped>
.container {
  margin-top: 10vh;
}
.dropdown {
  position: relative;
  display: inline-block;
}

.dropdown-content {
  display: none;
  position: absolute;
  background-color: #f9f9f9;
  min-width: 160px;
  box-shadow: 0px 8px 16px 0px rgba(0, 0, 0, 0.2);
  padding: 12px 16px;
  z-index: 1;
}
.dropdown:hover .dropdown-content {
  display: block;
}
</style>
