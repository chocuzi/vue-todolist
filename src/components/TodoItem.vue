<template>
  <div class="todo-list">
    <ul>
      <li v-for="todo in todos" :key="todo.id" class="animate__animated animate__backInRight ">
        <div class="circle" :class="todo.complated ? 'active' : ''">
          <input
            type="checkbox"
            :checked="todo.complated"
            @change="$emit('change-checkbox', todo.id)"
          />
        </div>
        <span v-show="!todo.bool" 
          :class="todo.complated ? 'active' : ''" class="contet-text" 
          @dblclick.self="dblHandler(todo.id)"
          >
          {{ todo.title }}
        </span>
        <input v-show="todo.bool" type="text" :value="todo.title" 
        class="search-input" @blur="$emit('blur-text',todo.id,$event)" />
        <div class="remo-todo">
          <button @click="$emit('remove-todo', todo.id)">×</button>
        </div>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: "TodoItem",
  props: ["todos"],
  data:function(){
   return {bool:true}
  },
  methods: {
    dblHandler(id){
      this.$emit('abc-c',this.bool,id)
    },
   
  },
};
</script>

<style scoped>
@import "https://cdnjs.cloudflare.com/ajax/libs/animate.css/4.1.1/animate.min.css";

.todo-list {
  width: 552px;
  box-sizing: border-box;
  overflow: hidden;
}
.todo-list ul {
  margin: 0;
  padding: 0;
  width: 100%;
}
.todo-list ul li {
  width: calc(100% - 2px);
  height: 58px;
  list-style: none;
  border: 1px solid #ccc;
  margin-top: -1px;
  overflow: hidden;
}
/* .todo-list ul li > * {
  float: left;
} */
.todo-list ul li span {
  float: left;
  display: block;
  transition: color 0.4s;
}
.todo-list ul li .circle {
  float: left;
  position: relative;
  display: block;
  width: 30px;
  height: 30px;
  margin: 14px;
  border-radius: 50%;
  border: 1px solid #ccc;
}
.todo-list ul li .remo-todo {
  float: right;
  width: 40px;
  height: 40px;
  margin: 9px;
}
.todo-list ul li .remo-todo button {
  display: block;
  width: 100%;
  height: 100%;
  margin: 0;
  padding: 0;
  outline: #ccc;
  border: 0;
}
.todo-list ul li .circle > input {
  display: block;
  width: 100%;
  height: 100%;
  margin: 0;
  padding: 0;
  outline: none;
  border: 0px solid transparent;
  opacity: 0;
}
div.active {
  background: url(data:image/svg+xml;utf8,%3Csvg%20xmlns%3D%22http%3A//www.w3.org/2000/svg%22%20width%3D%2240%22%20height%3D%2240%22%20viewBox%3D%22-10%20-18%20100%20135%22%3E%3Ccircle%20cx%3D%2250%22%20cy%3D%2250%22%20r%3D%2250%22%20fill%3D%22none%22%20stroke%3D%22%23bddad5%22%20stroke-width%3D%223%22/%3E%3Cpath%20fill%3D%22%235dc2af%22%20d%3D%22M72%2025L42%2071%2027%2056l-4%204%2020%2020%2034-52z%22/%3E%3C/svg%3E);
  background-position: -8px -5px;
}
.contet-text{
    float: left;
  display: block;
  width: calc(100% - 130px);
  height: 35px;
  line-height: 35px;
  margin: 14px 0; 

}
span.active {
  text-decoration: line-through;
}
.search-input{
  float: left;
  display: block;
  width: calc(100% - 150px);
  height: 35px;
  margin: 9px 0; 
  padding: 0 10px;
  border: 1px solid #ccc;
  outline: #ccc;
}
</style>