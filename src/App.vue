<template>
  <div id="app">
    <div class="img"><img class="img" src="./assets/5.png" alt=""></div>
    <input v-model="myValue" type="text">
    <button @click="handleIt">Submit</button>

    <ul>
      <!--          mycontent后面的item就是变量-->
      <todo-global-component
        v-for="(item,index) of myList"
        :key="index"
        :mycontent="item"
        :index="index"
        :class="{active:stateCurrent != index}"
        @delete="handleDelete">

      </todo-global-component>
    </ul>
  </div>

</template>

<script>

import Todolist from './components/Todolist'

export default {
  // name: 'App',
  components: {
    'todo-global-component': Todolist
  },
  data () {
    return {
      myValue: '',
      myList: [],
      stateCurrent: 999
    }
  },
  methods: {
    handleIt () {
      this.myList.push(this.myValue)
      this.myValue = ''
    },
    handleDelete (index) {
      this.myList.splice(index, 1)
    }
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
  .img{
    width: 400px;
    margin: 0 auto;
  }
  .active{
    background-color: #42b983;
}
</style>
