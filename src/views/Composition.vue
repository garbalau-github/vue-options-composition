<template>
  <div class="home">
    <img alt="Vue logo" src="../assets/logo.png" />
    <h3>You have {{ todoLength }} todos</h3>
    <div>
      <input
        @keyup.enter="addTodo"
        v-model="state.newTodoName"
        type="text"
        placeholder="Add a todo"
      />
    </div>
    <div>
      <ul>
        <li :key="todo.id" v-for="(todo, index) in state.todos">
          <span>{{ todo.name }}</span>
          <button @click="deleteTodo(index)">X</button>
        </li>
      </ul>
    </div>
  </div>
</template>

<script>
import { reactive, computed, watch } from 'vue';
export default {
  setup() {
    let state = reactive({
      newTodoName: '',
      todos: [],
    });
    let todoLength = computed(() => {
      return state.todos.length;
    });
    const swearwords = ['fuck', 'ass', 'shit'];
    function addTodo() {
      if (state.newTodoName) {
        const newTodo = {
          id: Date.now(),
          name: state.newTodoName,
        };
        state.todos.push(newTodo);
        state.newTodoName = '';
      }
    }
    function deleteTodo(index) {
      state.todos.splice(index, 1);
    }
    watch(state, (newValue) => {
      if (swearwords.includes(newValue.newTodoName.toLowerCase())) {
        state.newTodoName = '';
        alert(`You must never use ${newValue.newTodoName}!`);
      }
    });
    return {
      state,
      todoLength,
      addTodo,
      deleteTodo,
    };
  },
};
</script>
