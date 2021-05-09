<template>
    <li>
        {{todo.description}}

        <div class="buttons">
            <button class="concluido">Concluído</button>                       
            <button class="remover">Remover</button>                       
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