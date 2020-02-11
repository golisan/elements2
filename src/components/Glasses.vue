<template>
  <div>
    <b-button v-on:click="addGlas" variant="outline-primary">+</b-button>
    <div ref="container"></div>
  </div>
</template>

<script>
import WaterCan from "../components/WaterCan";
import Vue from "vue";
export default {
  name: "Glasses",

  props: {
    amount: {
      type: Number,
      default: 0
    }
  },
  created() {
    console.log("Glasses/create; amount:", this.amount);
    //this.createGlasses(this.amount);
  },
  mounted() {
    console.log("Glasses/mounted; amount:", this.amount);
    this.createGlasses(this.amount);
  },
  methods: {
    createGlasses: function(amount) {
      console.log("Glasses/createGlasses; amount:", amount);
      let i = 0;
      for (i = 0; i < amount; i++) {
        var ComponentClass = Vue.extend(WaterCan);
        var instance = new ComponentClass({
          propsData: { value: 0 }
        });
        instance.$mount(); // pass nothing
        console.log(this.$refs);
        this.$refs.container.appendChild(instance.$el);
      }
    },

    addGlas: function() {
      console.log("Glasses/addGlas");
      var ComponentClass = Vue.extend(WaterCan);
      var instance = new ComponentClass({
        propsData: { value: 0 }
      });
      instance.$mount(); // pass nothing
      console.log(this.$refs);
      this.$refs.container.appendChild(instance.$el);
    }
  }
};
</script>

<style>
</style>