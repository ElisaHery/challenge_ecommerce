<template>
     <div>
        <div>
            <input type="checkbox" id="football" value="football" v-model="checked_themes"/>
            <label for="football">Football</label>
        </div>
         <div>
            <input type="checkbox" id="femmes" value="femmes" v-model="checked_themes"/>
            <label for="femmes">Femmes</label>
        </div>
          <div>
            <input type="checkbox" id="alcool" value="alcool" v-model="checked_themes"/>
            <label for="alcool">Alcool</label>
        </div>
         <div>
            <input type="checkbox" id="papa" value="papa" v-model="checked_themes"/>
            <label for="papa">Jeune papa</label>
        </div>
        <div>
            <input type="checkbox" value="autres" id="autres" v-model="checked_themes"/>
            <label for="autres">Autres </label>
        </div>
    </div>
</template>

    <script>
export default {
  data() {
    return {
      checked_themes: []
    };
  },
  updated() {
    // console.log(this.checked_themes);
    this.$ebus.$emit("checked_themes", this.checked_themes);
  }
};
</script>
    
    