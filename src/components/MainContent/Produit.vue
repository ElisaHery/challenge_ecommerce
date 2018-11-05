<template>
<div class="under_main">
 <div class="produit"  v-for="(product, n) in products" :key="n" 
 >
 <!-- v-if="this.price_limit > product.price"  -->
 <img class="image" :src="product.src">
<p class="product_name">{{product.name}}</p>

<p class="product_price">{{product.price}} €</p>

    </div>
</div>
   
</template>

<script>
export default {
  data() {
    return {
      price_limit: 40
    };
  },
  props: ["products"],

  methods: {
    getLimit(msg_name) {
      this.$ebus.$on(msg_name, payload => {
        console.log(payload.classe);
        this.customMessage = payload.message;
        this.customClass = payload.classe;
        console.log(this.customMessage);
      });
    }
  }
};
</script>


<style lang="scss">
.under_main {
  cursor: pointer;
  display: flex;
  flex-wrap: wrap;
  height: 100%;
  width: 100%;
}
.product_name {
  color: black;
  margin: 5px;
}
.product_price {
  color: black;
  margin: 3px;
}
.produit {
  background: white;
  height: 320px;
  margin: 10px;
  width: 250px;
}

.image {
  height: 250px;
  transition: 0.3s;
  &:hover {
    height: 300px;
  }
}
</style>