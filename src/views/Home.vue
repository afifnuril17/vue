<template>
  <div class="parent">
    <v-row class="mb-6">
      <v-col sm="5" md="3">
        <v-row sm="5" md="6">
          <v-col sm="5" md="12">
            <v-card class="cardDate" tile>
              <div class="heigth"></div>
              <div>
                <div class="d-flex justify-center">
                  <img
                    src="https://assets.pikiran-rakyat.com/crop/0x0:0x0/x/photo/2020/12/11/3973959611.jpg"
                    alt=""
                    style="
                      width: 80px;
                      height: 80px;
                      border-radius: 50%;
                      object-fit: cover;
                      margin-top: -30px;
                    "
                  />
                </div>
                <h4>Paul McCarteny</h4>
                <h5>Kota Jakarta Pusat</h5>
              </div>
            </v-card>
          </v-col>
        </v-row>
        <v-card class="cardGraphLeft">
          <div class="margin">
            <v-row sm="5" md="6">
              <v-icon class="icon" size="20px">mdi-alarm</v-icon>
              <h3>Home</h3>
            </v-row>
          </div>

          <div class="margin">
            <v-row sm="5" md="6">
              <v-icon class="icon" size="20px">mdi-alarm</v-icon>
              <h3>Conseling</h3>
            </v-row>
          </div>
          <div class="margin">
            <v-row sm="5" md="6">
              <v-icon class="icon" size="20px">mdi-alarm</v-icon>
              <h3>Mood Tracker</h3>
              <v-icon class="icon" size="20px">mdi-alarm</v-icon>
            </v-row>
          </div>
          <div class="margin">
            <v-row sm="5" md="6">
              <v-icon class="icon" size="20px">mdi-alarm</v-icon>
              <h3>Library</h3>
            </v-row>
          </div>
          <div class="margin">
            <v-row sm="5" md="6">
              <v-icon class="icon" size="20px">mdi-alarm</v-icon>
              <h3>Quiz</h3>
            </v-row>
          </div>
          <div class="margin">
            <v-row sm="5" md="6">
              <v-icon class="icon" size="20px">mdi-alarm</v-icon>
              <h3>Event</h3>
            </v-row>
          </div>
        </v-card>
      </v-col>
      <v-col sm="5" md="9">
        <v-card class="cardGraphRight" tile>
          <v-card class="cardGraphRight2" tile>
            <h3 class="txtBagimanaEmosi">Bagaimana Perasaanmu?</h3>
            <div
              v-for="(i, index) in dataEmosi"
              :key="index"
              class="justify-center d-flex flex-wrap"
            >
              <div class="emosiView">{{ i.label }}</div>
            </div>
          </v-card>
        </v-card>
      </v-col>
    </v-row>
    <a href="/about">ABout</a>
    <a href="/chart">Chart</a>
    <!-- <buat-contoh @trigger="homeTrigger" /> -->
    <!-- <hello-world :title="title" /> -->
  </div>
</template>

<script>
import BuatContoh from "../components/BuatContoh.vue";
import HelloWorld from "../components/HelloWorld";

export default {
  name: "Home",
  data() {
    return {
      title: [
        {
          text: "title",
        },
      ],
      startDate: "",
      endDate: "",
      dataEmosi: [
        {
          id: 1,
          label: "Tenang",
        },
        {
          id: 2,
          label: "Santai",
        },
        {
          id: 1,
          label: "Antusis",
        },
        {
          id: 1,
          label: "Percaya Diri",
        },
        {
          id: 1,
          label: "Fokus",
        },
        {
          id: 1,
          label: "Enrgik",
        },
        {
          id: 1,
          label: "Gembira",
        },
        {
          id: 1,
          label: "Bahagia",
        },
        {
          id: 1,
          label: "Bangga",
        },
        {
          id: 1,
          label: "Lelah",
        },
        {
          id: 1,
          label: "Tegang",
        },
        {
          id: 1,
          label: "Sedih",
        },
        {
          id: 1,
          label: "Grogi",
        },
        {
          id: 1,
          label: "Jengkel",
        },
        {
          id: 1,
          label: "Kesepian",
        },
        {
          id: 1,
          label: "Mati Rasa",
        },
        {
          id: 1,
          label: "Bersalah",
        },
      ],
    };
  },
  mounted() {
    const moment = require("moment");
    this.startDate = moment().locale("ID").format("dddd, LL");
  },
  methods: {
    homeTrigger() {
      console.log("home trigger");
    },
  },
  components: {
    HelloWorld,
    BuatContoh,
  },
};
</script>

<style scoped>
.parent {
  margin-top: 30px;
  margin-left: 20px;
  margin-right: 20px;
}
.heigth {
  height: 50px;
  background-color: pink;
}
.heigthui {
  padding: 20px;
}
.imgStyle {
  border-radius: 50%;
  margin-bottom: 10px;
  width: 80px;
  height: 80px;
  margin-top: -40px;
}
.titleWidth {
  width: 100%;
  background-color: red;
}
.cardTitle {
  justify-items: center;
  align-items: "center";
  padding: 5px;
  background-color: rgb(231, 231, 231);
}
.cardDate {
  text-align: center;
  font-size: 20px;
  border-radius: 10px;
}
.rowTotalProfit {
  text-align: center;
}
.txtProfit {
  text-align: right;
}
.txtProfitPersen {
  text-align: left;
  color: green;
}
.cardGraphLeft {
  /* height: 200px; */
  padding: 20px;
  padding-left: 40px;
  padding-right: 40px;
  margin-top: 20px;
  border-radius: 10px;
}
.cardGraphRight {
  height: 470px;
  padding: 20px;
}
.cardGraphRight2 {
  height: 430px;
  padding: 5px;
}
.emosiView {
  border-width: 1;
  padding: 10xp;
  margin-left: 10px;
  margin-right: 10px;
}
.txtBagimanaEmosi {
  text-align: center;
  font-size: 30px;
  margin-bottom: 30px;
}
.icon {
  margin-left: 10px;
  margin-right: 10px;
}
.margin {
  margin: 20px;
}
</style>
