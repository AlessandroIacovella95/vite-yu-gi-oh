<script>
import axios from "axios";
export default {
  data() {
    return {
      archetypes: [],
    };
  },

  methods: {
    fetchArchetypes() {
      axios
        .get("https://db.ygoprodeck.com/api/v7/archetypes.php")
        .then((response) => {
          this.archetypes = response.data;
        });
    },
    filterByArchetype() {
      this.$emit("archetype-selected", this.selectedArchetype);
    },
  },

  created() {
    this.fetchArchetypes();
  },
};
</script>
<template>
  <div>
    <select id="archetypeSelect" @change="filterByArchetype">
      <option value="">Tutti gli Archetipi</option>
      <option
        v-for="archetype in archetypes"
        :key="archetype"
        :value="archetype"
      >
        {{ archetype.archetype_name }}
      </option>
    </select>
  </div>
</template>

<style lang="scss" scoped></style>
