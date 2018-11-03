<template>
<div class="under_main">
 <div class="produit"  v-for="(product, n) in products" :key="n" 
 >
 <!-- v-if="this.price_limit > product.price"  -->
<p class="product_name">{{product.name}}</p>
<img class="image" :src="product.src">
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
  //   created() {
  //     this.$ebus.$on("price_limit", payload => {
  //       this.price_limit = payload;
  //       console.log(this.price_limit);
  //     });
  //   },

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
  display: flex;
  flex-wrap: wrap;
  height: 100%;
  width: 100%;
}
.product_name {
  color: white;
  margin: 5px;
}
.product_price {
  color: white;
  margin: 3px;
}

.produit {
  background: black;
  height: 240px;
  margin: 10px;
  width: 250px;
}

.image {
  height: 170px;
}
</style>