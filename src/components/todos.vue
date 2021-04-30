<template>
  <div>
    <CreateTodo :addTodo="addTodo"/>
    <h3>Todos List</h3>
    <div class="row" v-for="todo in todos" :key="todo.id">
      {{todo.id}}
      <input type="checkbox" v-model="todo.completed" />
      <p :style="[todo.completed ? { 'text-decoration': 'line-through' } : '']">
        {{ todo.description }}
      </p>
      <span class="priority">{{ todo.priority }}</span>
      <a href="#" @click="deleteTodo(todo.id)">Delete</a>
    </div>
  </div>
</template>

<script>
import CreateTodo from './createTodo'
export default {
  name: "Todos",
  components: {
      CreateTodo
  },
  data: () => {
    return {
      todos: [
        {
          id: 1,
          description:
            "Lorem ipsum dolor sit amet consectetur adipisicing elit.",
          priority: "Medium",
          completed: true,
        },
        {
          id: 2,
          description:
            "Nemo totam autem odit repellendus facilis quas dolor fugit.",
          priority: "High",
          completed: false,
        },
        {
          id: 3,
          description:
            "Tempora consectetur id qui repellat laboriosam alias sunt blanditiis ducimus, aliquam aut quis.",
          priority: "Low",
          completed: false,
        },
      ]
    };
  },
  methods: {
    deleteTodo: function (id) {
      console.log(`Deleting todo : ${id}`);
      this.todos = this.todos.filter((f) => f.id !== id);
    },
    addTodo: function(des, priority) {
        this.todos.push({ id: Math.max(...this.todos.map(m => m.id))+1, description: des, priority: priority, completed: false })
    }
  },
};
</script>

<style>
.row {
  width: 100%;
  margin: 0 20px;
}

.row > p {
  margin-left: 10px;
  display: inline-block;
  width: 75%;
}

.row span {
  width: 10%;
  display: inline-block;
}

.createTodo {
    width: 100%;
}

</style>