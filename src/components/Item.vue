<template>
  <div id="item">
    <p class="todo-item">
      {{ todo.title }}
      <button @click="$emit('del-todo',todo._id)" class="del">
        <i class="fa fa-trash"></i>
      </button>
    </p>
  </div>
</template>


<script>
export default {
  name: "item",
  props: ["todo"],
};
</script>

<style scoped>
.todo-item {
  background-color: #fff;
  padding: 10px;
  margin: 10px;
  border-radius: 5px;
  font-size: 20px;
}
.del {
  color: #df1a47;
  border: none;
  cursor: pointer;
  float: right;
  background-color: #fff;
  font-size: 25px;
}
</style>
