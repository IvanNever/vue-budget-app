<template>
  <div class="list-item-wrap">
    <div class="list-item" v-for="(item, prop) in list" :key="prop">
      <span class="budget-comment">{{ item.comment }}</span>
      <span class="budget-value" :class = "item.type === 'INCOME' ? 'income' : 'outcome'">
        <i :class="item.type === 'INCOME' ? 'el-icon-top' : 'el-icon-bottom'"></i>
        {{ item.value }}
      </span>
      <ElButton type="danger" size="mini" @click="deleteItem(item.id)">Delete</ElButton>
    </div>
  </div>
</template>

<script>
export default {
  name: "BudgetListItem",
  props: {
    list: {
      type: Object,
      default: () => ({}),
    },
  },
  computed: {

  },
  methods: {
    deleteItem(id) {
      this.$emit('deleteItem', id);
    },
  },
}
</script>

<style scoped>
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
.income {
  color: green;
}
.outcome {
  color: red;
}
</style>