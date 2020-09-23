<template>
  <div class="antialiased">
    <router-view />
  </div>
</template>

<script lang="ts">
import { defineComponent } from "vue";

export default defineComponent({
  name: "App"
});
</script>

<style>
@import "https://fonts.googleapis.com/css2?family=Raleway:wght@500;700&display=swap";
@import "https://fonts.googleapis.com/icon?family=Material+Icons";

body {
  font-family: "Raleway", sans-serif;
  height: 100vh;
}
</style>
