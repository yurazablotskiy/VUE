<template>
  <div class="header">
    <span class="logo">{{ title }}</span>
    <button @click="addRating">+</button>
    <span class="user">{{ fullName }} ({{ user.rating }})</span>
  </div>
</template>

<script>
export default {
  name: 'Header', 
  data() {
    return {
      user: {
        name: "John",
        surname: 'Doe',
        age: 20,
        rating: 0,
        email: 'john@gmail.com'
      },
      allRating: 0,
    }
  },
  computed: {
    fullName() {
      return `Hello, ${this.user.name} ${this.user.surname}`
    }
  },
  methods: {
    addRating() {
      this.user.rating++,
      this.allRating++
    }
  },
  mounted() {
    this.addRating()
  },
  watch: {
    allRating(newValue, oldValue) {
      if (newValue > 5) {
        console.log(`${newValue} - ${oldValue}`)
      }
    },
  },
  props: {
    title: {
      type: String,
      required: true,
    },
  }
};
</script>

<style scoped>
.header {
  background: #333;
  color: #fff;
  padding: 20px;
  border-bottom: 2px solid black;
}

.header .logo {
  font-size: 20px;
}

.header .user {
  float: right;
}

.header button {
  float: right;
  border: 0;
  background-color: #871717;
  border-radius: 5px;
  padding: 10px 15px;
  font-size: 10px;
  margin-left: 15px;
  position: relative;
  top: -5px;
  color: white;
}

.header button:hover {
  background-color: bisque;
  cursor: pointer;
  color: black;
}
</style>