<template>
  <q-layout view="lHh Lpr lFf">
    <SideBar />
    <q-page-container>
      <router-view />
    </q-page-container>
    <RightSideBar />
  </q-layout>
</template>

<script>
import { defineComponent } from "vue";
import SideBar from "./components/SideBar.vue";
import RightSideBar from "./components/RightSideBar.vue";

export default defineComponent({
  name: "App",
  components: {
    SideBar,
    RightSideBar,
  },
});
</script>
