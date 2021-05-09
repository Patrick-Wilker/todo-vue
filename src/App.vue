<template>
  <div id="app">
    <main>
        <h1>Adicione suas tarefas</h1>
        <form @submit.prevent="addTodo(todo)">
            <input type="text" v-model="todo.description" id="texto" name="texto" placeholder="Fazer compras" required="required"><br><br>
            <button type="submit" name="btnSalvar">Adicionar</button>
        </form>   

        <ul class="lista">
          <li v-for="t in todos" :key="t.id">
            {{t.description}}

            <div class="buttons">
                <button class="concluido">Concluído</button>                       
                <button class="remover">Remover</button>                       
            </div>
          </li>
        </ul>
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

main ul li+li{
    margin-top: 10px;
}

main ul li{
    list-style: none;
    display: flex;
    align-items: center;
    justify-content: space-between;
    
    background: rgba(0, 113, 227, 0.1);
    border-radius: 4px;
    padding: 5px 15px;
}
.buttons{
  min-width: 100px;
}
.buttons button{
  background: none;
  border: 0;
  font-weight: bold;
}
.buttons .concluido{
  color: blue;
  cursor: pointer;

}
.buttons .remover{
  color: red;
  cursor: pointer;
}
</style>
