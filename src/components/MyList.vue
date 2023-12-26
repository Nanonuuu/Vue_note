<template>
  <ul>
    <MyTodo
      v-for="todoObj in todos"
      :key="todoObj.id"
      :todo="todoObj"
      :changeMood="changeMood"
      :handleDelete="handleDelete"
      :selectAll="selectAll"
    />
  </ul>
</template>

<script>
import MyTodo from "./MyTodo";
export default {
  name: "MyList",
  components: { MyTodo },
  props: ["todos", "changeMood", "handleDelete", "selectAll"],
};
</script>

<style scoped>
/*main*/
.todo-main {
  margin-left: 0;
  border: 1px solid #ddd;
  border-radius: 2px;
  padding: 0px;
}

.todo-empty {
  height: 40px;
  line-height: 40px;
  border: 1px solid #ddd;
  border-radius: 2px;
  padding-left: 5px;
  margin-top: 10px;
}
</style>