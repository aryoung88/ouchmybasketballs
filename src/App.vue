<template>
  <!--<img alt="Vue logo" src="./assets/logo.png">-->
  <HelloWorld msg="Welcome to Your Vue.js App"/>
</template>

<script>
import HelloWorld from './components/HelloWorld.vue';
//import { Amplify, API, graphqlOperation } from 'aws-amplify';
import { Amplify, API } from 'aws-amplify';
import awsconfig from './aws-exports';
//import { createTodo, listTodos, updateTodo, deleteTodo } from './graphql/todo'
import { createTodo, listTodos  } from './graphql/todo';

Amplify.configure(awsconfig);
const result = await API.graphql(createTodo, {
  input: {
    name: 'My first todo!'
  }
})
await API.graphql(listTodos)
console.log(result)
export default {
  name: 'App',
  components: {
    HelloWorld,
  }
}
</script>

<style>
body {
	background-image: url('https://www.gannett-cdn.com/presto/2021/06/30/USAT/7da95164-480a-4b44-9ffd-06639d6ae8ad-giannis-injury.jpg?width=2160'); 
	background-size: cover;
	}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
