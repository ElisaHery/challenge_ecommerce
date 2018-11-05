    <template>
        <div class="color_wrap">
    
            <div class="input_color black" data-value="black" @click="getColor" v-bind:class="{ activeBlack: isActiveBlack }"></div> 
            <div class="input_color grey" data-value="grey" @click="getColor" v-bind:class="{ active: isActiveGrey }"></div>
            <div class="input_color blue" data-value="blue" @click="getColor" v-bind:class="{ active: isActiveBlue }"></div>
            <div class="input_color red" data-value="red" @click="getColor" v-bind:class="{ active: isActiveRed }"></div>
            <div class="input_color white" data-value="white" @click="getColor" v-bind:class="{ active: isActiveWhite }"></div>
    </div>
    </template>

    <script>
export default {
  data() {
    return {
      input_color: [],
      isActiveBlack: false,
      isActiveGrey: false,
      isActiveBlue: false,
      isActiveRed: false,
      isActiveWhite: false
    };
  },
  updated() {
    //console.log(this.price_limit);
    //this.$ebus.$emit("price_limit", this.price_limit);
  },
  methods: {
    //récupère la couleur cliquée
    getColor(event) {
      let selectedColor = event.srcElement.getAttribute("data-value");
      //

      console.log(this.isActiveblue);
      this.toggleActive(event.srcElement.getAttribute("data-value"));
      this.listInputColors(selectedColor);
      //   console.log(this.input_color);
    },

    toggleActive(color) {
      if (color === "black") {
        this.isActiveBlack = !this.isActiveBlack;
      } else if (color === "blue") {
        this.isActiveBlue = !this.isActiveBlue;
      } else if (color === "grey") {
        this.isActiveGrey = !this.isActiveGrey;
      } else if (color === "red") {
        this.isActiveRed = !this.isActiveRed;
      } else if (color === "white") {
        this.isActiveWhite = !this.isActiveWhite;
      }
    },
    //ajoute la couleur cliquée dans input_color, ou l'enlève s'il s'agit d'un second click
    listInputColors(color) {
      if (!this.input_color.includes(color)) {
        this.input_color.push(color);
        //console.log(this.input_color);
        this.$ebus.$emit("checked_colors", this.input_color);
      } else {
        let colorIndex = this.input_color.indexOf(color);
        this.input_color.splice(colorIndex, 1);
        //console.log(this.input_color);
        this.$ebus.$emit("checked_colors", this.input_color);
      }
    }
  }
};
</script>

<style lang="scss">
.color_wrap {
  display: flex;
  justify-content: center;
}

.input_color {
  cursor: pointer;
  height: 30px;
  margin: 3px;
  width: 30px;
  box-sizing: border-box;
}
.black {
  background: black;
}
.blue {
  background: #223f7f;
}
.grey {
  background: grey;
}
.red {
  background: #84354a;
}
.white {
  background: white;
}
.active {
  border: black 2px solid;
}
.activeBlack {
  border: grey 2px solid;
}
</style>

    