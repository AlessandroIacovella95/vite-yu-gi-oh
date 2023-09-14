<script>
import axios from "axios";
import { store } from "./data/store";
import BaseSelect from "./components/BaseSelect.vue";
import AppHeader from "./components/AppHeader.vue";
import AppMain from "./components/AppMain.vue";
import AppLoader from "./components/cards/AppLoader.vue";

export default {
  data() {
    return {
      store,
      isLoading: false,
    };
  },

  components: { AppHeader, AppMain, BaseSelect, AppLoader },

  methods: {
    fetchCards(endpoint) {
      this.isLoading = true;
      axios
        .get(endpoint)
        .then((response) => {
          store.cards = response.data.data;
        })
        .catch((error) => {
          console.error(error);
          store.cards = [];
        })
        .finally(() => {
          this.isLoading = false;
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
  <AppLoader loadingText="Loading Cards" v-if="isLoading" />
  <AppHeader />
  <BaseSelect class="select_archetype" @archetype-selected="handleChange" />
  <AppMain />
</template>

<style lang="scss">
@use "./assets/scss/style.scss";

.select_archetype {
  margin-left: 100px;
}
</style>
