<template>
  <div class="container">
    <h2 class="title">Products</h2>
    <div class="container-wrapper">
      <div v-for="(product, i) in data.products" :key="i">
        <Card :data="product" :sales="sales" :highest="highest" />
      </div>
    </div>
  </div>
</template>

<script>
import products from "@/json/products.json";
import Card from "@/components/Card.vue";
export default {
  name: "App",
  components: {
    Card,
  },
  data() {
    return {
      data: [],
      sales: [],
      highest: newQty.reduce((acc, shot) => (acc = acc > shot ? acc : shot), 0),
    };
  },
  created() {
    this.data = products;
    this.sales = products.sales;
    // this.highest = products.products.map((pro, i) => {
    //   // console.log(
    //   products.sales
    //     .filter((sale) => sale.product_id === pro.id)
    //     .reduce((acc, curr) => acc + curr.qty, 0);
    //   // );
    // });
  },
};
const newQty = [];
products.products.map((pro, i) => {
  newQty.push(
    products.sales
      .filter((sale) => sale.product_id === pro.id)
      .reduce((acc, curr) => acc + curr.qty, 0)
  );
});
console.log(newQty);
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
