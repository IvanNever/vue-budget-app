<template>
  <div class="total-value" :style="{'color': BalanceColor }">Balance: {{ totalBalance }}</div>
</template>

<script>
import { mapGetters } from 'vuex';

export default {
  name: 'TotalBalance',

  computed: {
    ...mapGetters("dataList", ["budgetList"]),

    totalBalance() {
      return Object.values(this.budgetList).reduce((acc, item) => acc + item.value, 0)
    },

    BalanceColor() {
      //todo: need to refactor
      const total = Object.values(this.budgetList).reduce((acc, item) => acc + item.value, 0);
      if (total === 0) {
        return "black";
      } else if (total  > 0) {
        return "green";
      } else {
        return "red";
      }
    },
  },

}
</script>

<style scoped>
.total-value {
  font-size: 26px;
  text-transform: uppercase;
  padding: 20px;
  text-align: center;
 }
</style>