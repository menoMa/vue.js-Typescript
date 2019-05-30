<template>
  <div>
    <form>
      <div>
        <label>タイトル</label>
        <input v-model="todoForm.title" type="text">
      </div>
      <div>
        <label>詳細</label>
        <input v-model="todoForm.description" type="text">
      </div>
    </form>
    <button v-on:click="createTodo">TODO作成</button>
    <p>{{ todoForm }}</p>
    <div>
      <ul>
        <li v-for="todo in todoList" :key="todo.title">
          <p>{{todo.title}}</p>
          <p>{{todo.description}}</p>
        </li>
      </ul>
    </div>
  </div>
</template>

<script lang="ts">
import { Component, Prop, Vue } from "vue-property-decorator";

interface TodoForm {
  title: string;
  description?: string;
}

@Component
export default class TodoList extends Vue {
  private todoForm: TodoForm = {
    title: "",
    description: ""
  };

  todoList: TodoForm[] = [];
  createTodo() {
    console.log("click");
    const todo = Object.assign({}, this.todoForm);
    this.todoList.push(todo);
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
</style>
