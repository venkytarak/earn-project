<template>
  <v-app>
    <SideBar/>
    <v-main>
      <v-container>
        <router-view
        ></router-view>
      </v-container>
    </v-main>
  </v-app>
</template>
<script>

import SideBar from './components/admin/SideBar.vue'

export default {
  name: "App",
  components: {  SideBar }, 
  data: () => ({
   
    drawer: null,
  }),
  methods: {},
};
</script>./components/admin/SideBar.vue./components/admin/SideBar.vue