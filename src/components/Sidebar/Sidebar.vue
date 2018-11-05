<template>
    <div id="side">
        <h2 class="text_sidebar">Filtrer</h2>
        <hr>
       
        <h3 class="text_sidebar">Prix maximum</h3>
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
  components: { inputRange, checkBox, inputColor }
};
</script>


<style lang="scss">
#side {
  background: #1f3c60;
  border-radius: 10px;
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