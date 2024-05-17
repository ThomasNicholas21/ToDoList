<template>
  <div class="todo-list">
    <h1>Lista de Tarefas</h1>
    <input v-model="newTask" @keyup.enter="addTask" placeholder="Adicione uma nova tarefa" />
    <button @click="addTask">Adicionar</button>
    <ul>
      <li v-for="(task, index) in tasks" :key="index">
        <span :class="{ done: task.done }">{{ task.text }}</span>
        <button @click="toggleDone(index)">Concluir</button>
        <button @click="removeTask(index)">Remover</button>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  data() {
    return {
      newTask: '',
      tasks: []
    };
  },
  methods: {
    addTask() {
      if (this.newTask.trim() !== '') {
        this.tasks.push({ text: this.newTask, done: false });
        this.newTask = '';
      }
    },
    toggleDone(index) {
      this.tasks[index].done = !this.tasks[index].done;
    },
    removeTask(index) {
      this.tasks.splice(index, 1);
    }
  }
};
</script>

<style scoped>
.todo-list {
  max-width: 400px;
  margin: 0 auto;
  text-align: center;
}
input {
  width: 80%;
  padding: 10px;
  margin-bottom: 10px;
}
button {
  margin: 5px;
}
.done {
  text-decoration: line-through;
}
</style>
