<script>
import axios from "axios";
import { store } from "./data/store";
import BaseSelect from "./components/BaseSelect.vue";
import AppHeader from "./components/AppHeader.vue";
import AppMain from "./components/AppMain.vue";

export default {
  data() {
    return {
      store,
    };
  },

  components: { AppHeader, AppMain, BaseSelect },

  methods: {
    fetchCards(endpoint) {
      axios.get(endpoint).then((response) => {
        store.cards = response.data.data;
      });
    },

    handleChange(selectedArchetype) {
      const newApiUri = `${"https://db.ygoprodeck.com/api/v7/cardinfo.php?"}archetype=${selectedArchetype}`;
      this.fetchCards(newApiUri);
    },
  },

  created() {
    this.fetchCards(store.apiUri);
  },
};
</script>

<template>
  <AppHeader />
  <BaseSelect @archetype-selected="handleChange" />
  <AppMain />
</template>

<style lang="scss">
@use "./assets/scss/style.scss";
</style>
