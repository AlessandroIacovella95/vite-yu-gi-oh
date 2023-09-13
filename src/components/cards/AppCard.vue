<script>
export default {
  props: {
    image_url_small: String,
    name: String,
    archetype: String,
  },
};
</script>

<template>
  <div class="col text-center">
    <div class="card_">
      <img :src="image_url_small" alt="" />
      <h6>{{ name }}</h6>
      <p>{{ archetype }}</p>
    </div>
  </div>
</template>

<style lang="scss" scoped>
.col {
  padding-bottom: 15px;
  display: flex;
  justify-content: center;
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
</style>
