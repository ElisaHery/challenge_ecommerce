    <template>
        <div>
            <span>0 € </span>
        <input type="range" min="0" max="40" v-model="price_limit">   
        <span>40 € </span>
        <p>{{this.price_limit}} €</p>
    </div>
    </template>

    <script>
export default {
  data() {
    return {
      price_limit: 0
    };
  },
  updated() {
    //console.log(this.price_limit);
    this.$ebus.$emit("price_limit", this.price_limit);
  }
};
</script>
    
    