<template>
  <h1
    class="pl-8 font-medium text-2xl sm:text-2xl md:text-4xl lg:text-5xl leading-tight border-l-8 border-accent"
  >
    “{{ quote }}”
  </h1>
</template>

<script lang="ts">
import { defineComponent } from "vue";

export default defineComponent({
  name: "Quote",
  props: {
    quote: {
      type: String,
      required: true
    }
  }
});
</script>
