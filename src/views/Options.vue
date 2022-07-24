<template>
  <div class="home">
    <img alt="Vue logo" src="../assets/logo.png" />
    <h3>You have {{ todoLength }} todos</h3>
    <div>
      <input
        @keyup.enter="addTodo"
        v-model="newTodoName"
        type="text"
        placeholder="Add a todo"
      />
    </div>
    <div>
      <ul>
        <li :key="todo.id" v-for="(todo, index) in todos">
          <span>{{ todo.name }}</span>
          <button @click="deleteTodo(index)">X</button>
        </li>
      </ul>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      newTodoName: '',
      todos: [
        {
          id: 1,
          name: 'Walk the dog',
        },
        {
          id: 2,
          name: 'Find a job',
        },
        {
          id: 3,
          name: 'Make a dinner',
        },
      ],
      swearwords: ['fuck', 'ass', 'shit'],
    };
  },
  computed: {
    todoLength() {
      return this.todos.length;
    },
  },
  methods: {
    addTodo() {
      const newTodo = {
        id: Date.now(),
        name: this.newTodoName,
      };
      this.todos.push(newTodo);
      this.newTodoName = '';
    },
    deleteTodo(index) {
      this.todos.splice(index, 1);
    },
  },
  watch: {
    newTodoName(newValue) {
      if (this.swearwords.includes(newValue.toLowerCase())) {
        this.newTodoName = '';
        alert(`You must never use ${newValue}!`);
      }
    },
  },
};
</script>
