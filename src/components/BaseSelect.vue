<script>
import axios from "axios";
export default {
  data() {
    return {
      selectedArchetype: "",
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

  emits: ["archetype-selected"],
};
</script>
<template>
  <div>
    <select
      id="archetypeSelect"
      @change="filterByArchetype"
      v-model="selectedArchetype"
    >
      <option value="">Tutti gli Archetipi</option>
      <option
        v-for="archetype in archetypes"
        :key="archetype"
        :value="archetype.archetype_name"
      >
        {{ archetype.archetype_name }}
      </option>
    </select>
  </div>
</template>

<style lang="scss" scoped></style>
