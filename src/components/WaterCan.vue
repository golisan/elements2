<template>
  <span @click="onClick($event)">
    <img style="width: 100px; height: 100px" :src="fillImage" />
  </span>
</template>

<script>
import fullGlas from "@/assets/images/waterglasfull.png";
import emptyGlas from "@/assets/images/waterglasempty.png";
import { bus } from "../main";
export default {
  name: "WaterCan",
  props: {
    value: {
      type: Number,
      default: 0
    }
  },
  mounted() {},
  data() {
    return {};
  },
  watch: {
    value(val) {
      console.log("watch", val);
    }
  },
  computed: {
    fillImage() {
      console.log("fillImage");
      return this.value === 100 ? fullGlas : emptyGlas;
    }
  },
  methods: {
    onClick() {
      console.log("vor onClick", this.value);
      if (this.value === 0) {
        this.value = 100;
        //this.$emit("input", 100);
        //this.$emit("watercanclick", 100);
        bus.$emit("watercanclick", 100);
      } else {
        this.value = 0;
        //this.$emit("input", 0);
        bus.$emit("watercanclick", 0);
        //        this.$emit("watercanclick", 0);
      }
      console.log("nach onClick", this.value);
    }
  }
};
</script>

<style scoped>
</style>
