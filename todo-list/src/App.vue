<template>
  <Header title="itProger" />
  <Articles />
</template>

<script>
import Header from './components/Header.vue';
import Articles from './components/Articles.vue';

export default {
  components: {
    Header, Articles,
  }
};
</script>

<style>
body {
  background-color: #fcfcfc;
}
</style>

