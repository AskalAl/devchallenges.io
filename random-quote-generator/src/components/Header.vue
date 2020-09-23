<template>
  <div class="w-full py-6">
    <Container>
      <div class="flex justify-end items-center">
        <button @click="callback" class="border-none focus:outline-none">
          <div class="flex justify-between items-center space-x-2">
            <span>random</span>
            <span class="material-icons">
              autorenew
            </span>
          </div>
        </button>
      </div>
    </Container>
  </div>
</template>

<script lang="ts">
import { defineComponent, PropType } from "vue";
import Container from "./Container.vue";

export default defineComponent({
  name: "Header",
  components: {
    Container
  },
  props: {
    callback: {
      type: Function as PropType<() => Promise<void> | (() => void)>,
      required: true
    }
  }
});
</script>
