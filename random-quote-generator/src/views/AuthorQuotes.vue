<template>
  <Header :callback="redirectHome" />
  <Container class="mt-20 mb-12">
    <div class="flex flex-wrap justify-center items-center">
      <div class="w-full mb-8">
        <router-link
          to="/"
          class="flex items-center space-x-8"
          :style="{ color: '#828282' }"
        >
          <span class="material-icons">
            navigate_before
          </span>
          <h1 class="font-medium text-2xl">
            Go Back
          </h1>
        </router-link>
      </div>
      <div class="w-full mb-12">
        <h1 class="font-bold text-dark text-4xl">{{ author }}</h1>
      </div>
      <div v-for="quote in quotes" :key="quote._id" class="w-full mb-32">
        <Quote :quote="quote.quoteText" />
      </div>
    </div>
  </Container>
  <Footer />
</template>

<script lang="ts">
import { defineComponent, onMounted, ref } from "vue";
import { useRoute, useRouter } from "vue-router";

import axios from "@/common/axios";
import { IQuote } from "@/common/quote";

import Header from "@/components/Header.vue";
import Footer from "@/components/Footer.vue";
import Container from "@/components/Container.vue";
import Quote from "@/components/Quote.vue";

export default defineComponent({
  name: "AuthorQuotes",
  components: {
    Header,
    Footer,
    Container,
    Quote
  },
  setup() {
    const route = useRoute();
    const router = useRouter();

    const quotes = ref<IQuote[]>([
      {
        _id: "",
        quoteText: "",
        quoteAuthor: "",
        quoteGenre: ""
      }
    ]);

    async function fetchAuthorQuotes() {
      const { data } = await axios.get(`/authors/${route.params.author}`);

      quotes.value = data.quotes;
    }

    onMounted(fetchAuthorQuotes);

    function redirectHome() {
      return router.push("/");
    }

    return {
      quotes,
      author: route.params.author,
      fetchAuthorQuotes,
      redirectHome
    };
  }
});
</script>
