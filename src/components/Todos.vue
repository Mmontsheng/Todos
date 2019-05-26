<template>
  <div id="todos">
    <div class="todoItems" >
      <div v-for="todo in todos" :key="todo._id">
        <Item v-bind:todo="todo" v-on:del-todo="$emit('del-todo',todo._id)"/>
      </div>
    </div>
  </div>
</template>

<script>
import Item from "@/components/Item";
export default {
  name: "todos",
  components: {
    Item
  },

  props: ["todos"]
};
</script>

<style scoped>
.todoItems {
  height: 310px;
  overflow-y: auto;
  background-color: #f4f4f4;
  border-radius: 5px;
}
</style>

