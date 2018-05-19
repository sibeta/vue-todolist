<template>
  <div class="header">
    <h1 v-text="title"></h1>
    <h1 v-text="titleFromParent"></h1>
    <button v-on:click="onClickMe">Click Me</button>
  </div>
</template>

<script>

export default {
  name: 'todoList',
  data: function () {
    return {
      title: 'Todo List'
    }
  },
  props: ['titleFromParent'],
  watch: {

  },
  methods: {
    onClickMe: function () {
      this.$emit('msg-from-header', this.title)
    }
  }
}
</script>

<style>
ul {
  /*list-style: none;*/
}
li {
  font-size: 20px;
  text-align: left;
}
a {
  color: #42b983;
  text-decoration: none;
}
.finished {
  text-decoration: line-through;
}
</style>
