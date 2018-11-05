<template>
  <div class="wrap">
    <h1>Sélectionner vos produits</h1>
    <div class="produits">
      <side-bar></side-bar>
      <main-content></main-content>

    </div>
    

  </div>
</template>

<script>
import mainContent from "@/components/MainContent/MainContent.vue";
import sideBar from "@/components/Sidebar/Sidebar.vue";
export default {
  components: {
    mainContent,
    sideBar
  }
};
</script>

<style lang="scss">
h1 {
  margin: 40px;
}
.produits {
  display: flex;
  height: auto;
  width: 100%;
}
</style>
