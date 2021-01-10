<template>
  <div id="app">
    <h1>todos</h1>
    <AddTodo @all-item="allItem" @add-item="addItem"></AddTodo>
    <TodoList
      :todos="currentStatus"
      @change-checkbox="change"
      @remove-todo="removeTodo"
      @ccc="dblChange"
      @ddd="blurHandler"

    >
    </TodoList>
    <ChangeStatus
      @change-status="changeStatu"
      @clear-todo="clearTodo"
      :length="currentActive.length"
      :allLength="todos.length"
    ></ChangeStatus>
  </div>
</template>

<script>
import TodoList from "./components/TodoList.vue";
import AddTodo from "./components/AddTodo.vue";
import ChangeStatus from "./components/ChangeStatus.vue";

export default {
  name: "App",
  components: {
    TodoList,
    AddTodo,
    ChangeStatus,
  },
  data: () => {
    return {
      status: "all",
      todos: [
        { title: "js", complated: true, id: 1 },
        { title: "vue", complated: false, id: 2 },
        { title: "react", complated: false, id: 3 },
      ],
    };
  },
  computed: {
    currentActive() {
      return this.todos.filter((todo) => !todo.complated);
    },
    currentComplated() {
      return this.todos.filter((todo) => todo.complated);
    },
    currentStatus() {
      switch (this.status) {
        case "active":
          return this.currentActive;
        case "complated":
          return this.currentComplated;
        default:
          return this.todos;
      }
    },

  },
  methods: {
    //切换选中状态
    change(id) {
      this.todos = this.todos.map((todo) => {
        if (todo.id === id) {
          return { ...todo, complated: !todo.complated };
        }
        return { ...todo };
      });
    },
    //全选
    allItem() {
      if (!this.currentActive.length) {
        this.todos = this.todos.map((todo) => {
          return { ...todo, complated: false };
        });
      } else {
        this.todos = this.todos.map((todo) => {
          return { ...todo, complated: true };
        });
      }
    },
    //添加
    addItem(text) {
      if (text.length == 0) {
        return;
      }
      this.todos.push({
        title: text,
        complated: false,
        id: this.todos.length ? this.todos[this.todos.length - 1].id + 1 : 0,
      });
    },
    //删除
    removeTodo(id) {
      this.todos = this.todos.filter((todo) => {
        return todo.id !== id;
      });
    },
    //切换状态
    changeStatu(status) {
      this.status = status;
    },
    clearTodo() {
      // console.log(this.currentActive);
      this.todos = this.currentActive;
    },
    dblChange(bool,id){
      this.todos = this.todos.map((todo) => {
        if (todo.id === id) {
          return { ...todo, bool: bool };
        }
        return { ...todo };
      });
    },
    blurHandler(id,e){
        this.todos = this.todos.map((todo) => {
        if (todo.id === id) {
          return { ...todo, bool: false,title:e.target.value };
        }
        return { ...todo };
      });
    }
  },
};
</script>

<style>
#app {
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
}
h1 {
  position: absolute;
  top: -200px;
  width: 100%;
  font-size: 100px;
  font-weight: 100;
  text-align: center;
  /* color: rgba(175, 47, 47, 0.15); */
  -webkit-text-rendering: optimizeLegibility;
  -moz-text-rendering: optimizeLegibility;
  text-rendering: optimizeLegibility;
}
</style>
