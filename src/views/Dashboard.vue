<template>
  <div>
    <hr />
    <b-container fluid>
      <b-row>
        <b-col>
          <DateSelector></DateSelector>
        </b-col>
      </b-row>
    </b-container>
    <hr />
    <b-container fluid>
      <b-row>
        <b-col>
          <div class="totalscore">Gesamtpunktzahl: {{ totalScore }}</div>
          <div class="text-right">
            <b-button pill variant="success">Bonus</b-button>
          </div>
        </b-col>
      </b-row>
      <b-row>
        <b-col>
          <a>Es verbleiben für heute noch {{ restpoints }} Punkte</a>
        </b-col>
      </b-row>
      <b-row>
        <b-col>
          <img class="w-50 p-3" :src="fillImage" />
        </b-col>
      </b-row>
      <b-row>
        <b-col>
          <Glasses :amount="5"></Glasses>
        </b-col>
      </b-row>
    </b-container>
  </div>
</template>

<script>
import { bus } from "../main";
import sun from "@/assets/images/sun.png";
import DateSelector from "../components/DateSelector";
import Glasses from "../components/Glasses";
export default {
  components: { DateSelector, Glasses },
  data: function() {
    return {
      totalScore: 10
    };
  },
  created() {
    bus.$on("newdate", value => {
      console.log("bus/newdate", value);
    });
  },

  computed: {
    fillImage() {
      console.log("fillImage");
      return sun;
    },
    restpoints() {
      return 30 - this.totalScore;
    }
  }
};
</script>

<style scoped>
.totalscore {
  float: left;
}
.bonus {
  float: right;
}
</style>
