<template>
  <div id="app">
    <main>
        <h1>Adicione suas tarefas</h1>
        <form @submit.prevent="addTodo(todo)">
            <input type="text" v-model="todo.description" id="texto" name="texto" placeholder="Fazer compras" required="required"><br><br>
            <button type="submit" name="btnSalvar">Adicionar</button>
        </form>   

        <ul class="lista">
          <Todo v-for="t in todos" :key="t.id" @toggle="toggleTodo" @remove="removeTodo" :todo="t"/>
        </ul>
    </main>
  </div>
</template>

<script>
import Todo from './components/Todo'
export default {
  name: 'App',
  components: {Todo: Todo},
  data(){
    return {todos: [], todo: {checked: false}};
  },
  methods: {
    addTodo(todo){
      todo.id = Date.now();
      this.todos.push(todo);
      this.todo = {checked: false};
    },

    toggleTodo(todo){
      const index = this.todos.findIndex(item => item.id === todo.id)
      if(index > -1){
        const checked = !this.todos[index].checked
        this.$set(this.todos, index, {...this.todos[index], checked})
      }
    },

    removeTodo(todo){
      const index = this.todos.findIndex(item => item.id === todo.id)
      if(index > -1){
        this.$delete(this.todos, index)
      }
    }
  }
}
</script>

<style>
#app {
  font-family: Roboto, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

p, li, a, h1{
  word-break: break-all;
}

a{
    text-decoration: none;
    color: black;
    cursor: pointer;
}
main{
    text-align: center;
    max-width: 700px;
    margin: auto;
}

main form{
    display: flex;
    align-items: center;
    justify-content: center;
}
main form input{
    padding: 6px 10px;
    color: #1c1c1c;
    border: 1px solid rgba(0,0,0,0.5);
    border-radius: 4px;
    width: 70%;
}
main form button{
    padding: 8px 10px;
    background: #07BC0C;
    color: #fff;
    font-weight: bold;
    border: 0;
    border-radius: 4px;
    margin-left: 10px;
    transition: 0.5s;

    width: 30%;
}
main form button:hover{
    cursor: pointer;
    background: #069b08;
}
main ul{
    margin-top: 50px;
    padding: 0;
}

</style>
