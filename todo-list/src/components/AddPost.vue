<template>
  <form @submit.prevent="createPost" :class="{ error: maxCharacters > 20 }">
    <label for="title">Назавние статьи: </label>
    <input v-model="userTitleInput" type="text" id="title" placeholder="Введите название">
    <label for="text">Основной текст: <span>{{ maxCharacters }} / 20</span></label>
    <textarea v-model="userTextInput" id="text" placeholder="Введите текст"></textarea>
    <button>Добавить</button>
  </form>
</template>

<script>
export default {
  name: 'AddPost',
  data() {
    return {
      userTitleInput: '',
      userTextInput: '',
    }
  },
  methods: {
    createPost() {
      if (this.userTitleInput != '' && this.userTextInput != '') {
        this.$emit('add-post', this.userTitleInput, this.userTextInput);

        this.userTitleInput = '';
        this.userTextInput = '';
      }
    }
  },
  computed: {
    maxCharacters() {
      return this.userTextInput.length;
    }
  }
}
</script>

<style scoped>
form {
  margin-top: 20px;
}

form.error label {
  color: red;
}

form label {
  color: #505050;
}

form input,
form textarea {
  width: 100%;
  background-color: #c6c391;
  border-radius: 5px;
  border: 2px solid #5e5b21;
  padding: 8px 10px;
  font-size: 14px;
  color: #5e5b21;
  outline: none;
  margin-bottom: 10px;
  resize: none;
}

form button {
  float: right;
  background-color: #aaa771;
  border: 2px solid #5e5b21;
  border-bottom-width: 4px;
  padding: 10px 12px;
  font-size: 13px;
  font-weight: bold;
  color: #5e5b21;
  border-radius: 5px;
  cursor: pointer;
  transition: all 500ms ease;
}


form button:hover {
  margin-top: 2px;
  border-bottom-width: 2px;
}
</style>