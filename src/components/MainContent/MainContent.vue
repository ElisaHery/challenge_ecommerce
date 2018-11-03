<template>
    <div class="main">
<produit :products="filteredProducts"> </produit>
    </div>
</template>

<script>
import Produit from "./Produit.vue";
export default {
  data() {
    return {
      products: [
        {
          name: "tshirt1",
          price: 20,
          src: require("@/assets/tshirt1.jpg"),
          theme: "autres",
          color: "blue"
        },
        {
          name: "tshirt2",
          price: 30,
          src: require("@/assets/tshirt2.jpg"),
          theme: "alcool",
          color: "red"
        },
        {
          name: "tshirt3",
          price: 15,
          src: require("@/assets/tshirt3.jpg"),
          theme: "autres",
          color: "white"
        },
        {
          name: "tshirt4",
          price: 25,
          src: require("@/assets/tshirt4.jpg"),
          theme: "alcool",
          color: "blue"
        },
        {
          name: "tshirt5",
          price: 25,
          src: require("@/assets/tshirt5.jpg"),
          theme: "alcool",
          color: "blue"
        },
        {
          name: "tshirt8",
          price: 35,
          src: require("@/assets/tshirt8.jpg"),
          theme: "football",
          color: "grey"
        },
        {
          name: "tshirt11",
          price: 40,
          src: require("@/assets/tshirt11.jpg"),
          theme: "football",
          color: "blue"
        }
      ],
      price_limit: "",
      checked_themes: [],
      checked_colors: []
    };
  },
  //récupère les bus event pour le prix, le thème, et la couleur
  created() {
    this.$ebus.$on("price_limit", payload => {
      this.price_limit = payload;
      //console.log(this.price_limit);
    });
    this.$ebus.$on("checked_themes", payload => {
      this.checked_themes = payload;
      //console.log(this.price_limit);
    });
    this.$ebus.$on("checked_colors", payload => {
      this.checked_colors = payload;
      console.log(this.checked_colors);
    });
  },

  // filtre le tableau "products" en fonction des input de l'user
  computed: {
    filteredProducts: function() {
      //aucun filtre sélectionné
      if (
        this.price_limit.length === 0 &&
        this.checked_themes.length === 0 &&
        this.checked_colors.length === 0
      ) {
        return this.products;
        // filtre prix seul actif
      } else if (
        this.price_limit.length !== 0 &&
        this.checked_themes.length === 0 &&
        this.checked_colors.length === 0
      ) {
        return this.products.filter(product => {
          return product.price > this.price_limit;
        });
        //filtre thème seul actif
      } else if (
        this.price_limit.length === 0 &&
        this.checked_themes.length !== 0 &&
        this.checked_colors.length === 0
      ) {
        return this.products.filter(product => {
          return this.checked_themes.includes(product.theme);
        });

        //filtre couleur seul actif
      } else if (
        this.price_limit.length === 0 &&
        this.checked_themes.length === 0 &&
        this.checked_colors.length !== 0
      ) {
        return this.products.filter(product => {
          return this.checked_colors.includes(product.color);
        });

        //filtre prix et thème actifs
      } else if (
        this.price_limit.length !== 0 &&
        this.checked_themes.length !== 0 &&
        this.checked_colors.length === 0
      ) {
        return this.products.filter(product => {
          return (
            product.price > this.price_limit &&
            this.checked_themes.includes(product.theme)
          );
        });

        //filtre prix et couleur actifs
      } else if (
        this.price_limit.length !== 0 &&
        this.checked_themes.length === 0 &&
        this.checked_colors.length !== 0
      ) {
        return this.products.filter(product => {
          return (
            product.price > this.price_limit &&
            this.checked_colors.includes(product.color)
          );
        });

        //filtre thème et couleur actifs
      } else if (
        this.price_limit.length === 0 &&
        this.checked_themes.length !== 0 &&
        this.checked_colors.length !== 0
      ) {
        return this.products.filter(product => {
          return (
            this.checked_themes.includes(product.theme) &&
            this.checked_colors.includes(product.color)
          );
        });

        //filtres prix thème et couleur actifs
      } else {
        return this.products.filter(product => {
          return (
            product.price > this.price_limit &&
            this.checked_themes.includes(product.theme) &&
            this.checked_colors.includes(product.color)
          );
        });
      }
    }
  },

  components: {
    Produit
  }
};
</script>


<style lang="scss">
.main {
  background: grey;
  display: flex;
  height: auto;
  margin: 10px;
  width: 70%;
}
</style>