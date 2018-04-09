<template>
  <div id="app">
    <h1>todos</h1>
    <div class="input-box">
      <input placeholder="请输入内容" @keyup.enter="addTodo"/>
    </div>
    <Item
      v-for="todo in todos"
      :todo="todo"
      :key="todo.id"
      :onDelete="onDelete"
     />
  </div>
</template>

<script>
import Item from "./components/Item.vue";

let id = 2;
export default {
  name: "app",
  components: {
    Item
  },
  data() {
    return {
      todos: [
        {
          id: 1,
          content: "one ",
          completed: false
        }
      ]
    };
  },
  methods: {
    // 添加一条todo 事项
    addTodo(e) {
      this.todos.unshift({
        id: id++,
        content: e.target.value,
        completed: false
      });
      e.target.value = "";
    },
    // 删除一条todo事项
    onDelete(id) {
      this.todos = this.todos.filter(val => val.id !== id);
      console.log("you want delete", id);
    }
  }
};
</script>

<style>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
.input-box {
  margin-bottom: 20px;
}
.input-box input {
    width: 260px;
    height: 30px;
    line-height: 30px;
    font-size: 15px;
    /* border-radius: 5px; */
    border: 0;
    outline: 0;
    border-bottom: 1px solid #333;
  }
</style>
