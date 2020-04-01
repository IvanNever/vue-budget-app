<template>
    <div class="list-item" >
      <span class="budget-comment">{{ item.comment }}</span>
      <span class="budget-value" :class = "item.type === 'INCOME' ? 'income' : 'outcome'">
        <i :class="item.type === 'INCOME' ? 'el-icon-top' : 'el-icon-bottom'"></i>
        {{ item.value }}
      </span>
      <ElButton type="danger" size="mini" @click="deleteItem(item.id)">Delete</ElButton>
    </div>
</template>

<script>
import { mapActions } from "vuex";

export default {
  name: "BudgetListItem",
  props: {
    item: {
      type: Object,
      default: () => ({}),
    },
  },
  methods: {
    ...mapActions('dataList', ['onDeleteItem']),
    deleteItem(id) {
      const confirmDelete = confirm ('Are you sure?');
      if (confirmDelete) {
        this.onDeleteItem(id);
      } else { return }

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