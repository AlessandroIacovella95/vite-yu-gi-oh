<script>
import { store } from "../../data/store";
import AppCard from "./AppCard.vue";
export default {
  data() {
    return {
      store,
    };
  },
  components: { AppCard },
};
</script>

<template>
  <section>
    <div class="founded container">
      <span>Found 20 cards</span>
    </div>
    <div class="container">
      <div class="row g-3 row-cols-2 row-cols-md-3 row-cols-lg-5">
        <AppCard
          v-for="card in store.cards"
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
    background-color: #212529 !important;
    color: white !important;
    padding: 10px 0;
    margin: 15px auto;
    span {
      margin-left: 15px;
    }
  }

  .container {
    background-color: white;
  }
}
</style>
