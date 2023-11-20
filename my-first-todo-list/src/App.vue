<template>
  <div class="to-do-block">
    <h1>Список дел</h1>
    <p>Добавьте в список новые значения</p>
    <form @submit.prevent="addToDo">
      <input v-model="inputText" type="text" placeholder="Введите текст">
      <button>Добавить дело</button>
    </form>
    <ul class="to-do-list" v-for="el, i in toDoList">
      <li>{{ el }}</li>
      <button @click="deleteToDo(i)">Удалить</button>
    </ul>
  </div>
</template>

<script>
export default {
  inputText: '',
  data() {
    return {
      toDoList: [],
    }
  },
  methods: {
    addToDo() {
      this.toDoList.unshift(this.inputText.trim());
    },
    deleteToDo(i) {
      this.toDoList = this.toDoList.filter((el, index) => index != i)
    }
  }
}
</script>

<style>
.to-do-block {
  margin-top: 50px;
  text-align: center;
}

.to-do-block h1, p {
  font-weight: 600;
  font-family: sans-serif;
}

.to-do-block p {
  font-weight: 400;
  font-family: sans-serif;
}

form input {
  height: 30px;
  border-radius: 3px;
  outline: none;
  border: 1px solid black;
}
form button,
ul.to-do-list button {
  height: 30px;
  border-radius: 3px;
  background-color: rgb(49, 55, 55);
  color: white;
  margin-left: 3px;
  cursor: pointer;
  transition: background 500ms ease;
  border-bottom-width: 4px;
}
form button:hover,
ul.to-do-list button:hover {
  background-color: rgb(85, 84, 81);
  border-bottom-width: 2px;
}
ul.to-do-list {
  display: flex;
  justify-content: center;
  list-style: none;
  font-family: sans-serif;
}
ul li {
  margin-right: 20px;
}
</style>

