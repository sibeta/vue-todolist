<template>
  <div class="todoList">
    <input type="text" name="item" v-model="newItem" @keyup.enter="addItem">
    <ul>
      <li v-bind:class="{finished:item.isFinished}" :key="item.id" v-for="item in items" v-on:click="toggleFinish(item)" v-on:mouseenter="toggleDel(item)">{{item.label}}</li>
    </ul>
  </div>
</template>

<script>
import Store from '../store'

export default {
  name: 'todoList',
  data: function () {
    return {
      title: 'Todo List',
      items: Store.fetch(),
      newItem: ''
    }
  },
  watch: {
    items: {
      handler: function (items) {
        Store.save(items)
      },
      deep: true
    }
  },
  methods: {
    toggleFinish: function (item) {
      item.isFinished = !item.isFinished
    },
    addItem: function () {
      this.items.push({
        id: 1,
        label: this.newItem,
        isFinished: false,
        isDelete: false
      })
      this.newItem = ''
    },
    toggleDel: function (item) {

    }
  }
}
</script>

<style>
input {
  border: 1px solid #42b983;
  border-radius: 2px;
  font-size: 20px;
  height: 30px;
  line-height: 30px;
  outline: none;
}
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
