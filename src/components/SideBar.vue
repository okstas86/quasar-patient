<template>
  <q-drawer
    show-if-above
    side="left"
    behavior="desktop"
    :width="90"
    class="colorBackground"
  >
    <div class="flex flex-center column q-mt-lg q-mb-lg">
      <q-icon name="fas fa-box" size="md" style="color: #adf8a6" />
    </div>
    <div class="flex flex-center column q-mt-sm q-mb-md">
      <q-list>
        <q-item
          clicable
          :active="link === 'home'"
          @click="link = 'home'"
          active-class=""
        >
          <q-item-section avatar class="flex flex-center column">
            <q-icon name="fas fa-tachometer-alt" />
          </q-item-section>
        </q-item>
        <q-item
          clicable
          :active="link === 'clib'"
          @click="link = 'clib'"
          active-class=""
        >
          <q-item-section avatar class="flex flex-center column">
            <q-icon name="fas fa-clipboard" />
          </q-item-section>
        </q-item>
        <q-item
          clicable
          :active="link === 'commemt'"
          @click="link = 'comment'"
          active-class=""
        >
          <q-item-section avatar class="flex flex-center column">
            <q-icon name="fas fa-comments" />
          </q-item-section>
        </q-item>
        <q-item
          clicable
          :active="link === 'chart'"
          @click="link = 'chart'"
          active-class=""
        >
          <q-item-section avatar class="flex flex-center column">
            <q-icon name="fas fa-chart-bar" />
          </q-item-section>
        </q-item>
        <q-item
          clicable
          :active="link === 'cog'"
          @click="link = 'cog'"
          active-class=""
        >
          <q-item-section avatar class="flex flex-center column">
            <q-icon name="fas fa-cog" />
          </q-item-section>
        </q-item>
      </q-list>
    </div>
    <div
      style="
        position: absolute;
        bottom: 20px;
        margin-left: auto;
        left: 0;
        right: 0;
        text-align: center;
      "
    >
      <q-avatar>
        <img src="https://cdn.quasar.dev/img/avatar6.jpg" />
      </q-avatar>
      <div>
        <q-icon
          name="fas fa-user-plus"
          size="20px"
          color="white"
          class="q-my-md"
        />
      </div>
      <q-icon
        name="fas fa-sign-out-alt"
        size="20px"
        color="white"
        class="q-my-md"
      />
    </div>
  </q-drawer>
</template>

<script setup>
import { ref } from "vue";
const link = ref("home");
</script>

<style>
.colorBackground {
  background: #8ac186;
}
.q-item__section--side {
  padding-right: 0px !important;
}
.q-item__section--avatar {
  color: white !important;
}
.q-item {
  padding: 16px 0px !important;
}
</style>
