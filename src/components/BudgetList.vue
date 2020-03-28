<template>
  <div class="budget-list-wrap">
    <ElCard :header="header">
      <div class="filter-buttons">
        <el-button type="success">Income</el-button>
        <el-button type="danger">Outcome</el-button>
        <el-button type="primary">All items</el-button>
      </div>
      <template v-if="!isEmpty">
        <div v-for="(item, prop) in list" :key="prop">
          <BudgetListItem  :item="item" @deleteItem="SetDeleteItem"/>
        </div>
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
  methods: {
    SetDeleteItem(id) {
      this.$emit('deleteItem', id);
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
.filter-buttons {
  display: flex;
  justify-content: space-evenly;
  margin-bottom: 20px;
}
</style>