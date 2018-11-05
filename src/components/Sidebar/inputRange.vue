    <template>
        <div>
            
        <input type="range" min="0" max="40" v-model="price_limit">   
        
        <p class="text_sidebar">{{this.price_limit}} €</p>
    </div>
    </template>

    <script>
export default {
  data() {
    return {
      price_limit: 40
    };
  },
  updated() {
    //console.log(this.price_limit);
    this.$ebus.$emit("price_limit", this.price_limit);
  }
};
</script>
    
    