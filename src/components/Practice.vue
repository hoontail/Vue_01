<template>
  <div id="hello">
    <div>{{ msg }}</div>
    <form @submit.prevent="addTodo">
      <input v-model="newTodo" />
      <button>추가하기</button>
    </form>
    <div v-for="(todo, i) in hideTodos" :key="i">
      <input type="checkbox" v-model="todo.done" />
      <span :class="{ done: todo.done }">{{ todo.text }}</span>
      <!-- done: todo.done 하면 이렇게 의존하는건가??? -->
      <button @click="removeTodo(todo)">x</button>
    </div>
    <button @click="completed = !completed">
      {{ completed ? "전부확인" : "완료숨기기" }}
    </button>
  </div>
</template>

<script lang="ts">
import { defineComponent } from "vue";

let id = 0;
export default defineComponent({
  name: "HelloWorld",
  props: {
    msg: String,
  },

  data: function () {
    return {
      completed: false,
      newTodo: "",
      todos: [
        { id: id++, text: "JavaScript 배우기", done: false },
        { id: id++, text: "Vue 배우기", done: false },
        { id: id++, text: "무언가 멋진 것을 만들기", done: false },
      ],
    };
  },
  methods: {
    addTodo() {
      this.todos.push({ id: id++, text: this.newTodo, done: false });
      this.newTodo = "";
    },
    removeTodo(todo: { id: number; text: string }) {
      this.todos = this.todos.filter((t) => t !== todo);
    },
  },
  computed: {
    hideTodos() {
      return this.completed ? this.todos.filter((t) => !t.done) : this.todos;
    },
  },
});
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
div {
  padding: 15px;
}
.done {
  text-decoration: line-through;
}
</style>
