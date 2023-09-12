<script>
import axios from "axios";
import AppCard from "./AppCard.vue";
export default {
  data() {
    return {
      cards: [],
    };
  },

  components: { AppCard },

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
    <div class="founded">
      <span>Found 39 cards</span>
    </div>
    <div class="container">
      <div class="row g-3 row-cols-2 row-cols-md-3 row-cols-lg-5">
        <AppCard
          v-for="card in cards"
          :key="card.id"
          :image_url_small="card.card_images[0].image_url_small"
          :name="card.name"
          :archetype="card.archetype"
        />
      </div>
    </div>
  </section>
</template>

<style lang="scss" scoped>
section {
  background-color: #d48f38;
  padding: 50px 0;

  .founded {
    background-color: #212529;
    color: white;
    padding: 10px 0;
    width: 960px;
    margin: 15px auto;
  }

  .container {
    background-color: white;
    .col {
      padding-bottom: 15px;
      .card_ {
        height: 100%;
        width: 168px;
        background-color: #d48f38;

        img {
          max-width: 100%;
        }

        h6 {
          margin-top: 10px;
          color: white;
          font-weight: 700;
        }

        p {
          font-weight: 500;
        }
      }
    }
  }
}
</style>
