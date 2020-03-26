<template>
  <div class="budget-list-wrap">
    <ElCard :header="header">
      <template v-if="!isEmpty">
        <BudgetListItem :list="list"/>
      </template>
      <ElAlert v-else type="info" :title="emptyTitle" :closable="false"/>
    </ElCard>
  </div>
</template>

<script>
import BudgetListItem from '@/components/BudgetListItem';
export default {
  name: "BudgetList",
  components: {
    BudgetListItem,
  },
  props: {
    list: {
      type: Object,
      default: () => ({}),
    },
  },
  data: () => ({
    header: "Budget List",
    emptyTitle: "Empty List",
  }),
  computed: {
    isEmpty() {
      return !Object.keys(this.list).length;
    },
  },
}
</script>

<style scoped>
.budget-list-wrap {
  max-width: 500px;
  margin: auto;
}
.list-item {
  display: flex;
  align-items: center;
  padding: 10px 15px;
}
.budget-value {
  font-weight: bold;
  margin-left: auto;
  padding-right: 20px;
}
</style>