<template>
  <div>
    <v-container>
      <v-col cols="2" class="d-flex" style="flex-direction: column">
        <v-card class="mb-1 flex-grow-1"> Upper card </v-card>
        <v-card class="mt-1 flex-grow-1" height="100%px"> Lower card </v-card>
      </v-col>
    </v-container>
  </div>
</template>

<script>
export default {
  props: ["title"],
};
</script>

<style scoped>
.redColor {
  color: red;
}
.rowParent {
  background-color: yellow;
  flex: 1;
}
.row1 {
  background-color: aqua;
  flex: 1;
}
.row2 {
  background-color: blue;
  flex: 1;
}
</style>
