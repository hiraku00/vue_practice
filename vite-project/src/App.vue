<template>
  <div class="body">
    <div class="chap01">
      <h1>Vue 3</h1>
      <p>123 + 456 = {{ answer }}</p>
      <p
        v-html="message"
        :style="{ 'background-color': welcomeColor, color: 'white' }"
      ></p>
      <p>お名前は？： <input type="text" size="30" v-model="myname" /></p>
    </div>

    <br />

    <div class="chap02">
      <input type="text" size="30" v-model="number" />
      <button @click="add()">+1</button>
    </div>

    <br />

    <div class="chap03">
      <AppHeader color="pink">My ToDo</AppHeader>
      <input type="text" size="30" v-model="newToDo" />
      <button @click="addTodo()">追加</button>
      <TodoList :todos="todos" @removeTodo="removeTodo"/>
    </div>
  </div>
</template>

<script setup>
import AppHeader from "./components/AppHeader.vue";
import TodoList from "./components/TodoList.vue";
import { ref, computed } from "vue";

// chap01
const answer = computed(() => {
  return 123 + 456;
});

const message = computed(() => {
  return "hello <strong>" + myname.value + "</strong>";
});

const welcomeColor = ref("blue");
const myname = ref("");

// chap02
const number = ref(0);

const add = () => {
  number.value++;
};

// chap03&04
const newToDo = ref("");
const todos = ref([]);

const addTodo = () => {
  todos.value.push(newToDo.value);
  newToDo.value = "";
};

// chap04
const removeTodo = (index) => {
  todos.value.splice(index, 1);
};
</script>

<style>
body {
  font-family: sans-serif;
}
</style>
