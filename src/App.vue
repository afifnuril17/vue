<template>
  <div class="bgParent">
    <v-app>
      <v-main>
        <v-app-bar color="white">
          <v-img
            lazy-src="https://picsum.photos/id/11/10/6"
            max-height="120"
            max-width="120"
            src="http://dev-pam.gamifindo.com/img/logo-transparent.f18a8a11.png"
          ></v-img>
          <v-spacer></v-spacer>

          <v-img
            lazy-src="https://picsum.photos/id/11/10/6"
            max-height="50"
            max-width="50"
            contain
            class="imgStyle"
            src="https://assets.pikiran-rakyat.com/crop/0x0:0x0/x/photo/2020/12/11/3973959611.jpg"
          ></v-img>
        </v-app-bar>
        <router-view />
      </v-main>
    </v-app>
  </div>
</template>

<script>
export default {
  name: "App",

  data() {
    return {
      items: [
        { title: "Dashboard", icon: "mdi-view-dashboard" },
        { title: "Photos", icon: "mdi-image" },
        { title: "About", icon: "mdi-help-box" },
      ],
      right: null,
    };
  },
};
</script>

<style scoped>
.bgParent {
  background-color: rgb(231, 231, 231);
  min-height: 100vh;
  /* height: 925px; */
}
.alignText {
  text-align: center;
}
.imgStyle {
  border-radius: 50%;
}
</style>
