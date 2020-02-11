<template>
  <div>
    <WaterCan v-model="currentState"></WaterCan>
    <div>
      <h1>Ich habe heute {{ ml }} ml getrunken</h1>
    </div>

    <hr />
    <br />
    <a>Wieviele Gläser brauchst Du?</a>
    <br />
    <input type="radio" id="voll" :value="100" v-model="picked" />
    <label for="voll">Voll</label>
    <input type="radio" id="leer" :value="0" v-model="picked" />
    <label for="leer">Leer</label>
    <br />
    <input v-model="count" placeholder="Anzahl Gläser" />
    <button v-on:click="doIt">OK</button>
    <br />
    <div>Ich habe {{ mlGesamt }} getrunken</div>
    <div ref="glasses"></div>
  </div>
</template>

<script>
import WaterCan from "../components/WaterCan";
import Vue from "vue";
import { bus } from "../main";

export default {
  name: "Elements",
  components: { WaterCan },
  data: function() {
    return {
      ml: 0,
      mlGesamt: 0,
      currentState: 0,
      count: 0,
      picked: 0
    };
  },
  created() {
    bus.$on("watercanclick", value => {
      console.log("bus");
      if (value == 100) {
        this.mlGesamt = this.mlGesamt + 100;
      } else {
        this.mlGesamt = this.mlGesamt - 100;
      }
    });
  },
  watch: {
    currentState(newValue, oldValue) {
      if (oldValue < newValue) this.ml = this.ml + 100;
      else this.ml = this.ml - 100;
    }
  },
  methods: {
    doIt: function() {
      console.log("doit", this.picked);
      if (this.count > 0) {
        let i = 0;
        this.mlGesamt = 0;
        for (i = 0; i < this.count; i++) {
          var ComponentClass = Vue.extend(WaterCan);
          var instance = new ComponentClass({
            propsData: { value: this.picked }
          });
          instance.$mount(); // pass nothing
          this.$refs.glasses.appendChild(instance.$el);
        }
      }
    },
    doClick: function(value) {
      console.log("doClick", value);
      if (value == 100) {
        this.mlGesamt = this.mlGesamt + 100;
      } else {
        this.mlGesamt = this.mlGesamt - 100;
      }
    }
  }
};
</script >

<style scoped>
.empty {
  background-color: white;
}
.full {
  background-color: blue;
}
</style>