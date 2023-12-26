<template>
  <div class="todo-footer" v-show="totalnum > 0">
    <label>
      <!-- <input type="checkbox" :checked="check" @click="changeAll" /> -->
      <input type="checkbox" v-model="check" />
    </label>
    <span>
      <span>已完成{{ finishnum }}</span> / 全部{{ totalnum }}</span
    >
    <button class="btn btn-danger">清除已完成任务</button>
  </div>
</template>

<script>
export default {
  name: "MyFooter",
  props: ["todos", "selectAll"],
  computed: {
    totalnum() {
      return this.todos.length;
    },
    finishnum() {
      return this.todos.filter((todo) => todo.done == true).length;
    },
    // check() {
    //   return this.finishnum === this.totalnum && this.finishnum !== 0;
    // },
    check: {
      get() {
        return this.finishnum === this.totalnum && this.finishnum !== 0;
      },
      set(e) {
        this.selectAll(e); //e注意要么为true，要么为false，因为你是把它应用在了checkbox上
      },
    },
  },
  // methods: {
  //   changeAll(e) {
  //     this.selectAll(e.target.checked);
  //   },
  // },
};
</script>

<style scoped>
/*footer*/
.todo-footer {
  height: 40px;
  line-height: 40px;
  padding-left: 6px;
  margin-top: 5px;
}

.todo-footer label {
  display: inline-block;
  margin-right: 20px;
  cursor: pointer;
}

.todo-footer label input {
  position: relative;
  top: -1px;
  vertical-align: middle;
  margin-right: 5px;
}

.todo-footer button {
  float: right;
  margin-top: 5px;
}
</style>