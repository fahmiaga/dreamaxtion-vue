<template>
  <div class="card">
    <div class="card-wrapper">
      <div :class="data.stock < 10 ? 'item-stock danger-bg' : 'item-stock'">
        <h2 :class="data.stock < 10 ? 'danger' : ''">{{ data.stock }}</h2>
      </div>
      <div class="description">
        <h4>{{ data.product }}</h4>
        <div class="total-sold">
          <p>Total Sold</p>
          <p :class="data.sold === highest ? 'success' : ''">{{ data.sold }}</p>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: ["data", "highest"],
};
</script>

<style>
.card {
  width: 120px;
  height: auto;
  background-color: white;
  border-radius: 5px;
  box-shadow: 0 0 8px rgba(0, 0, 0, 0.2);
  cursor: pointer;
  border: 1px solid #f2f8f9;
  position: relative;
}

.card:hover {
  border: 0.1px solid #1c7947;
  transition: 1s;
}

.card-wrapper {
  width: 70px;
  margin: auto;
  padding: 5px;
}
.item-stock {
  width: 70px;
  height: 70px;
  background-color: #effffb;
  border-radius: 5px;
}

.item-stock h2 {
  text-align: center;
  line-height: 70px;
  color: #1597e5;
}

.description h4 {
  font-size: 0.65rem;
  margin-bottom: 0;
}
.description .total-sold {
  width: 70px;
  display: flex;
  justify-content: space-between;
}
.description .total-sold p {
  font-weight: 600;
  font-size: 0.55rem;
}
.description .total-sold p:nth-child(2) {
  padding: 1px 5px;
  border-radius: 5px;
  font-weight: 700;
  background-color: #e1e8eb;
}

.danger {
  color: #ec5858 !important;
}

.success {
  background-color: #caf7e3 !important;
  color: #39a388;
}

.danger-bg {
  background-color: #ffccd2;
}

/* responsive */

@media screen and (max-width: 600px) {
  .card {
    width: 240px;
    margin-bottom: 10px;
  }
  .card-wrapper {
    width: 100%;
    display: flex;
    justify-content: start;
  }
  .item-stock {
    margin-left: 20px;
    margin-right: 20px;
  }
  .item-stock h2 {
    line-height: 30px;
    text-align: center;
  }
}
</style>
