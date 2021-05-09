<template>
    <li :class="{checked: todo.checked}">
        {{todo.description}}
        <div class="buttons">
            <button @click="$emit('toggle', todo)" class="concluido">
            <span v-if="todo.checked">Desmarcar</span>
            <span v-else>Concluído</span>
            </button>                       
            <button @click="$emit('remove', todo)" class="remover">Remover</button>                       
        </div>
    </li>
</template>

<script>
export default{
    props: {
        todo: {type: Object, required: true}
    }
}
</script>

<style scoped>
li+li{
    margin-top: 10px;
}

li{
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

.checked{
    text-decoration: line-through;
    color: lightgray;
}
</style>