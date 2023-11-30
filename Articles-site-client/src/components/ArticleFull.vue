<template>
  <div class="item-full">
    <button @click="hideFullArticle"> Назад ко всем статьям </button>
    <img :src="articleData.img">
    <h2>{{ articleData.title }}</h2>
    <p>
      {{ articleData.full_text }}
    </p>
  </div>

  <div class="comments-block">
    <h3>Комментарии ({{ postData.length }})</h3>
    <CommentItem v-for="(comment, index) in postData" :key="index" :postData="comment" />
    <CommentsForm v-on:add-post="addComment" />
  </div>
</template>

<script>

import CommentItem from './CommentItem.vue';
import CommentsForm from './CommentsForm.vue';

export default {

  components: {
    CommentItem,
    CommentsForm
  },
  emits: ['hide-full-article'],
  data() {
    return {
      postData: [],
      showValue: true,
    }
  },
  props: {
    articleData: {},
  },
  methods: {
    hideFullArticle() {
      this.fullArticle = false
      this.$emit('hide-full-article', this.fullArticle);
    },
    addComment(name, text) {
     this.postData.unshift({name, text})
    }
  },
}
</script>

<style>
.item-full {
  height: 600px;
}

.item-full button {
  margin-top: 30px;
  background-color: rgba(181, 28, 28, 0.903);
  height: 40px;
  padding: 10px;
  font-size: 14px;
  border-radius: 5px;
  color: white;
  cursor: pointer;
  transition: all 500ms ease;
}

button:hover {
  background-color: rgba(138, 24, 24, 0.903);
}

.item-full img {
  display: block;
  margin-top: 35px;
  width: 1200px;
  height: 40%;
  object-fit: cover;
  border-radius: 10px;
}

.item-full h2 {
  margin-top: 20px;
  font-size: 32px;
}

.item-full p {
  line-height: 35px;
  margin-top: 20px;
  font-size: 20px;
}

.comments-block {
  width: 50%;
  margin-top: 70px;
}
</style>