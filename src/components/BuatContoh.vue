<template>
  <div>
    <v-app-bar dense flat outlined prominent shaped></v-app-bar>
    <h1 class="redColor">{{ title }}</h1>
    <input v-model="isiText" type="text" class="textInput" />

    <div v-if="list.length == 0">
      <h1>length 0</h1>
    </div>
    <v-card elevation="2" loading></v-card>
    <div class="exChild">
      <div v-for="(i, index) in list" :key="index">
        <p>{{ i }}</p>
      </div>
      <v-btn @click="addList">Add</v-btn>
      <v-btn @click="$emit('trigger')">Add Home</v-btn>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      title: "titlecotioh",
      isiText: "",
      list: [],
    };
  },
  mounted() {
    this.changeTitle();
    console.log("ndandiqnidq");
  },
  methods: {
    changeTitle() {
      var text = "ini";
      this.title = text;
    },
    addList() {
      if (this.isiText) {
        this.list.push(this.isiText);
        this.isiText = "";
      }
    },
  },
};
</script>

<style scoped>
.textInput {
  border: 1px black solid;
}
.ex {
  align-items: center;
  justify-items: center;
  align-content: center;
  justify-content: flex-end;
}
.exChild {
  margin-left: 25%;
  margin-right: 25%;
  width: 50%;
}
</style>
