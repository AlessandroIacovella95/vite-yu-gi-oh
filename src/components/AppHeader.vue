<script>
export default {
  data() {
    return {
      title: "Yu-Gi-Oh Api",
    };
  },
};
</script>

<template>
  <div class="container mt-3">
    <img class="img-fluid" src="/pngegg.png" alt="logo" />
    <h1 class="ms-3">{{ title }}</h1>
  </div>
</template>

<style lang="scss" scoped>
.container {
  display: flex;
  align-items: center;
  img {
    width: 100px;
  }
  h1 {
    font-size: 2rem;
  }
}
</style>
