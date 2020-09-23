<template>
  <Header :callback="fetchQuote" />
  <Container class="mt-20 mb-12">
    <div class="flex flex-wrap justify-center items-center">
      <div class="w-full">
        <Quote :quote="quote.quoteText" />
      </div>
      <div class="w-full mt-20 bg-dark px-8 py-12 cursor-pointer">
        <router-link :to="`/${quote.quoteAuthor}`">
          <div class="flex justify-between items-center">
            <div>
              <h1
                class="font-bold text-white text-xl sm:text-2xl leading-tight"
              >
                {{ quote.quoteAuthor }}
              </h1>
              <h4 class="font-medium text-lg" :style="{ color: '#828282' }">
                {{ quote.quoteGenre }}
              </h4>
            </div>
            <span class="material-icons text-white text-4xl select-none">
              arrow_right_alt
            </span>
          </div>
        </router-link>
      </div>
    </div>
  </Container>
  <Footer />
</template>

<script lang="ts">
import { defineComponent, onMounted, ref } from "vue";

import axios from "@/common/axios";
import { IQuote } from "@/common/quote";

import Header from "@/components/Header.vue";
import Footer from "@/components/Footer.vue";
import Container from "@/components/Container.vue";
import Quote from "@/components/Quote.vue";

export default defineComponent({
  name: "Home",
  components: {
    Header,
    Footer,
    Container,
    Quote
  },
  setup() {
    const quote = ref<IQuote>({
      quoteText: "",
      quoteAuthor: "",
      quoteGenre: ""
    });

    async function fetchQuote() {
      const { data } = await axios.get("/quotes/random");

      quote.value = { ...quote.value, ...data.quote };
    }

    onMounted(fetchQuote);

    return {
      quote,
      fetchQuote
    };
  }
});
</script>
