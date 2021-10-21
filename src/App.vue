<template>
  <div class="container">
    <h2 class="title">Products</h2>
    <div class="container-wrapper">
      <div v-for="(product, i) in data" :key="i">
        <Card :data="product" :highest="highest" />
      </div>
    </div>
  </div>
</template>

<script>
import products from "@/json/data.json";
import Card from "@/components/Card.vue";
export default {
  name: "App",
  components: {
    Card,
  },
  data() {
    return {
      data: [],
      highest: products.reduce(
        (acc, shot) => (acc = acc > shot.sold ? acc : shot.sold),
        0
      ),
    };
  },
  created() {
    this.data = products;
  },
};
</script>

<style>
body {
  margin: 0;
  padding: 0;
  background-color: #f1f6f9;
  font-family: "Poppins", sans-serif;
}
.container {
  width: 50%;
  margin: auto;
}
.container-wrapper {
  display: flex;
  justify-content: space-between;
}

@media screen and (max-width: 600px) {
  .container-wrapper {
    display: flex;
    justify-content: center;
    flex-direction: column;
    align-items: center;
  }
}
</style>
