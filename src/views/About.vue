<template>
  <div class="about">
    <v-card class="header" outlined tile>
      <v-row no-gutters>
        <v-col sm="2">
          <h4>No Transaksi</h4>
        </v-col>
        <v-col sm="2">
          <h4>Sesi ke</h4>
        </v-col>
        <v-col sm="2">
          <h4>Waktu Konseliong</h4>
        </v-col>
        <v-col sm="2">
          <h4>Status</h4>
        </v-col>
        <v-col sm="2">
          <h4></h4>
        </v-col>
        <v-col sm="2">
          <h4>Detail</h4>
        </v-col>
      </v-row>
    </v-card>

    <div v-for="n in dataEmosi" :key="n" class="context">
      <v-card class="header d-flex justify-center" outlined tile>
        <v-row no-gutters>
          <v-col sm="2">
            <h4>{{ n.id }}</h4>
          </v-col>
          <v-col sm="2">
            <h4>{{ n.no }}</h4>
          </v-col>
          <v-col sm="2">
            <h4>{{ require("moment")().locale("ID").format("dddd, LL") }}</h4>
          </v-col>
          <v-col sm="2">
            <v-btn v-if="n.status == true" class="blueColor"> Approved </v-btn>
            <v-btn v-else class="redColor"> Rejected </v-btn>
          </v-col>
          <v-col sm="2">
            <v-btn> Chat </v-btn>
          </v-col>
          <v-col sm="2">
            <v-btn color="red" class="brr">
              <v-icon size="20px">mdi-alarm</v-icon>
            </v-btn>
          </v-col>
        </v-row>
      </v-card>
    </div>
  </div>
</template>
<script lang="ts">
import Vue from "vue";
export default Vue.extend({
  data() {
    return {
      dataEmosi: [
        {
          id: "IN10129",
          no: 1,
          label: "Tenang",
          status: true,
        },
        {
          id: "IN101229",
          no: 2,
          status: true,
          label: "Santai",
        },
        { id: "IN10129A", label: "Antusis", no: 1, status: false },
        {
          id: "IN101S29",
          no: 1,
          status: false,
          label: "Percaya Diri",
        },
        {
          id: "IN101W29",
          no: 1,
          label: "Fokus",
          status: false,
        },
        {
          id: "IN101229",
          no: 1,
          label: "Enrgik",
          status: false,
        },
        {
          id: "IN101S29",
          no: 1,
          label: "Gembira",
          status: false,
        },
        {
          id: "IN1QWD0129",
          no: 1,
          label: "Bahagia",
          status: false,
        },
        {
          id: "IN10QWD129",
          no: 1,
          label: "Bangga",
          status: false,
        },
        {
          no: 1,
          id: "IN10QW129",
          label: "Lelah",
          status: false,
        },
        {
          no: 1,
          id: "IN101129",
          label: "Tegang",
          status: false,
        },
        {
          no: 1,
          id: "IN110129",
          label: "Sedih",
          status: false,
        },
        {
          id: "IN110129",
          no: 1,
          label: "Grogi",
          status: false,
        },
        {
          id: "IN1S0129",
          no: 1,
          label: "Jengkel",
          status: false,
        },
        {
          id: "IN10S129",
          no: 1,
          label: "Kesepian",
          status: false,
        },
        {
          id: "IN1W0129",
          no: 1,
          label: "Mati Rasa",
          status: false,
        },
        {
          no: 1,
          id: "IN101D29",
          label: "Bersalah",
          status: false,
        },
      ],
    };
  },
});
</script>

<style scoped>
.about {
  margin: 20px;
}
.header {
  padding: 10px;
  border-radius: 10px;
}
.context {
  margin-top: 10px;
}
.redColor {
  background-color: red;
  border-radius: 20px;
}
.blueColor {
  background-color: blue;
  border-radius: 20px;
}
.brr {
  border-radius: 100px;
  background-color: blue;
}
</style>
