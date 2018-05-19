<template>
  <div id="app">
    <vHeader titleFromParent="A Powerful ToDo Tool" v-on:msg-from-header="handleMsgFromHeader"></vHeader>
    <p>{{msgFromHeader}}<p/>
    <todoList></todoList>
  </div>
</template>

<script>
import vHeader from './components/Header'
import todoList from './components/TodoList'

export default {
  name: 'app',
  components: {
    vHeader,
    todoList
  },
  data: function () {
    return {
      msgFromHeader: ''
    }
  },
  methods: {
    handleMsgFromHeader: function (msg) {
      this.msgFromHeader = msg
    }
  }
}
</script>

<style>
#app {
  font-size: 14px;
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
body {
  display: flex;
  align-items: center;
  justify-content: center;
  height: 100%;
}
</style>
