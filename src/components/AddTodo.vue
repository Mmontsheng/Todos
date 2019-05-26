<template>
  <div id="add-todo">
    <form @submit.prevent="addTodo">
      <div class="add-form">
        <input class type="text" v-model="title" placeholder="Enter a todo...">
        <button class="btn btn-default" type="submit" value="add todo">
          <i class="fa fa-plus"></i>
        </button>
      </div>
      <p class="text-danger error" v-if="error">Enter todo first</p>
    </form>
  </div>
</template>


<script>
export default {
  name: "add",
  data() {
    return {
      title: "",
      id: 1,
      error: false
    };
  },
  methods: {
    addTodo() {
      if (this.title) {
        const newTodo = {
          //id: this.id++,
          title: this.title
        };

        this.$emit("add-todo", newTodo);
        this.title = null;
        this.error = false;
      } else {
        this.error = true;
      }
    }
  }
};
</script>

<style scoped>
.add-form {
  position: relative;
  margin-bottom: 7px;
} /*
.add-form input[type="text"] {
  width: 100%;
  padding: 12px 50px 12px 20px;
  background: #df1a47;
  color: white;
  outline: none;
  border: none;
  border-radius: 5px;
}
.add-form button {
  position: absolute;
  top: 5px;
  right: 5px;
  bottom: 5px;
  border: none;
  background: #fff;
  padding: 0px 15px;
  border-radius: 50%;
  color: #df1a47;
}
*/

.add-form input[type="text"] {
  width: 100%;
  padding: 15px 50px 15px 20px;
  background: #df1a47;
  color: white;
  outline: none;
border: none;
border-radius: 30px;
font-size: 17px;
}
.add-form button {
  position: absolute;
  top: 5px;
  right: 5px;
  bottom: 5px;
  padding: 0 40px;
  border: 2px solid #df1a47;
background: #fff;
border-radius: 30px;
color: #df1a47;
}
.add-form button:hover,
.add-form button:focus{
    background-color: #df1a47;
    color: #fff;
    border-color: #fff !important;
}

.text-danger {
  font-size: 12px;
  text-align: center;
}
</style>

