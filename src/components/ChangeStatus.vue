<template>
  <div id="footer" v-show="allLength">
    <div id="change-list">
      <div class="items-left">
        <span>{{ length }}items left</span>
      </div>
      <input type="button" @click="$emit('change-status', 'all')" value="all" />
      <input
        type="button"
        @click="$emit('change-status', 'active')"
        value="active"
      />
      <input
        type="button"
        @click="$emit('change-status', 'complated')"
        value="complated"
      />
      <input type="button" @click="$emit('clear-todo')" value="clear items" />
    </div>
  </div>
</template>

<script>
export default {
  name: "ChangeStatus",
  props: ["length", "allLength"],
};
</script>

<style>
#footer {
  /* width: 200px; */
  /* height: 80px; */
  margin-top: -1px;
}
#change-list {
  /* box-sizing: border-box; */
  width: 550px;
  height: 30px;
  margin: 0 auto;
  padding: 10px 0;
  border: 1px solid #ccc;
}
#change-list input {
  width: 80px;
  height: 30px;
  vertical-align: middle;
  margin-left: 30px;
  padding: 0;
  border: 0;
}
.items-left {
  display: inline-block;
  margin: 0 10px;
  line-height: 30px;
}
</style>