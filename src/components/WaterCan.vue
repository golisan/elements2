<template>
  <span @click="onClick($event)">
    <img style="width: 100px; height: 100px" :src="fillImage" />
  </span>
</template>

<script>
import fullGlas from "@/assets/images/waterglasfull.png";
import emptyGlas from "@/assets/images/waterglasempty.png";
export default {
  name: "WaterCan",
  props: {
    value: {
      type: Number,
      required: true,
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
      return this.value === 100 ? fullGlas : emptyGlas;
    }
  },
  methods: {
    onClick() {
      if (this.value === 0) {
        this.$emit("input", 100);
      } else {
        this.$emit("input", 0);
      }
    }
  }
};
</script>

<style scoped>
</style>
