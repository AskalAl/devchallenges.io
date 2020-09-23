<template>
  <div class="container mx-auto px-6 sm:px-12 md:px-32">
    <slot></slot>
  </div>
</template>

<script lang="ts">
import { defineComponent } from "vue";

export default defineComponent({
  name: "Container"
});
</script>
