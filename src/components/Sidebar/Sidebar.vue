<template>
    <div id="side">
        <h2 class="text_sidebar">Filtrer par</h2>
        <hr>
       
        <h3 class="text_sidebar">Prix</h3>
         <input-range/>
        <hr>
        <h3 class="text_sidebar">Thème</h3>
        <check-box/>

         <hr>
        <h3 class="text_sidebar">Couleur</h3>
        <input-color/>
    </div>
</template>

<script>
import inputRange from "@/components/Sidebar/inputRange.vue";
import checkBox from "@/components/Sidebar/inputCheckbox.vue";
import inputColor from "@/components/Sidebar/inputColor.vue";
export default {
  // data() {
  //   return {
  //     price_limit: 0
  //   };
  // },
  // updated() {
  //   //console.log(this.price_limit);
  //   this.$ebus.$emit("price_limit", this.price_limit);
  // },
  components: { inputRange, checkBox, inputColor }
};
</script>


<style lang="scss">
#side {
  background: grey;
  height: 600px;
  margin: 10px;
  width: 30%;
}

.text_sidebar {
  color: white;
}
hr {
  width: 80%;
}
</style>