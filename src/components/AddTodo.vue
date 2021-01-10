<template>
  <div>
    <div class="add-model">
      <div class="all-todo">
        <input
          class="all"
          type="button"
          value="all"
          @click="$emit('all-item')"
        />
      </div>
      <div class="new-input">
        <input
          placeholder="What needs to be done?"
          class="text"
          type="text"
          v-model.trim="text"
          @keyup.enter="addItem"
        />
      </div>
      <div class="add-todo">
        <input class="add" type="button" value="add" @click="addItem" />
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "AddTodo",
  props: [],
  data: () => {
    return { text: "" };
  },
  methods: {
    addItem() {
      this.$emit("add-item", this.text);
      this.text = "";
    },
  },
};
</script>

<style>
.add-model {
  width: 552px;
  margin: 0 auto;
  box-sizing: border-box;
  overflow: hidden;
  border: 1px solid #ccc;
}
.all-todo {
  float: left;
  width: 40px;
  height: 40px;
  margin: 9px;
}
.all-todo input,
.add-todo input {
  width: 40px;
  height: 40px;
  padding: 0;
  border: 0;
  outline: #ccc;
}
.add-todo {
  float: right;
  margin: 9px;
}
.new-input {
  float: left;
  width: 410px;
  height: 30px;
  margin: 14px 10px;
  border-bottom: 1px solid #ccc;
}
.new-input input {
  width: 100%;
  height: 100%;
  margin: 0;
  padding: 0;
  outline: none;
  border: none;
  font-size: 18px;
  background: rgba(0, 0, 0, 0.003);
  box-shadow: inset 0 -2px 1px rgba(0, 0, 0, 0.03);
}
</style>