<template>
  <div>
    <div id="todo-list">
      <TodoItem
        :todos="todos"
        @change-checkbox="$emit('change-checkbox', $event)"
        @remove-todo="$emit('remove-todo', $event)"
        @abc-c="dblChange"
        @blur-text="blurHandler"
      ></TodoItem>
    </div>
  </div>
</template>

<script>
import TodoItem from "./TodoItem.vue";

export default {
  name: "TodoList",
  props: ["todos"],
  components: {
    TodoItem,
  },
  data: () => {
    return {};
  },
  methods: {
    dblChange(bool,id){
      this.$emit("ccc",bool,id)
    },
    blurHandler(id,e){
      this.$emit("ddd",id,e)
    }
  },
};
</script>

<style>
#todo-list {
  width: 552px;
  overflow: hidden;
  margin: 0 auto;
}
</style>
