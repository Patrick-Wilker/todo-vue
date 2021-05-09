<template>
  <div id="app">
    <main>
        <h1>Adicione suas tarefas</h1>
        <form @submit.prevent="addTodo(todo)">
            <input type="text" v-model="todo.description" id="texto" name="texto" placeholder="Fazer compras" required="required"><br><br>
            <button type="submit" name="btnSalvar">Adicionar</button>
        </form>   
        {{todos}}
    </main>
  </div>
</template>

<script>

export default {
  name: 'App',
  data(){
    return {todos: [], todo: {checked: false}};
  },
  methods: {
    addTodo(todo){
      todo.id = Date.now();
      this.todos.push(todo);
      this.todo = {checked: false};
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
main{
    text-align: center;
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
}
main form button:hover{
    cursor: pointer;
    background: #069b08;
}
</style>
