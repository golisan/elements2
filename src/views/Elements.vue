<template>
  <div>
    <WaterCan v-model="currentState"></WaterCan>

    <div>
      <h1>Ich habe heute {{ ml }} ml getrunken</h1>
    </div>

    <i style="font-size: 50px; color: red;" class="el-icon-close" />
  </div>
</template>

<script>
import WaterCan from "../components/WaterCan";
export default {
  name: "Elements",
  components: { WaterCan },
  data: function() {
    return {
      ml: 0,
      currentState: 0
    };
  },

  watch: {
    currentState(newValue, oldValue) {
      if (oldValue < newValue) this.ml = this.ml + 100;
      else this.ml = this.ml - 100;
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