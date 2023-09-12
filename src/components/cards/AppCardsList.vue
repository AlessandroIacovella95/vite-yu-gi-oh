<script>
import axios from "axios";
export default {
  data() {
    return {
      cards: [],
    };
  },

  methods: {
    fetchCards() {
      axios
        .get("https://db.ygoprodeck.com/api/v7/cardinfo.php?num=20&offset=0")
        .then((response) => {
          this.cards = response.data.data;
        });
    },
  },

  created() {
    this.fetchCards();
  },
};
</script>

<template>
  <section>
    <div class="container">
      <div class="row g-4 row-cols-2 row-cols-md-3 row-cols-lg-4">
        <div class="col" v-for="card in cards">{{ card.name }}</div>
      </div>
    </div>
  </section>
</template>

<style lang="scss" scoped></style>
