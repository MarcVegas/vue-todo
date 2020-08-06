<template>
    <div>
        <div v-bind:key="item.id" v-for="item in todos">
            <TodoItem v-bind:item="item" v-on:delete-item="$emit('delete-item', item.id)" />
        </div>
    </div>
</template>

<script>
import TodoItem from './TodoItem'

export default {
    name: 'Todos',
    components: {
        TodoItem
    },
    props: ["todos"]
}
</script>

<style>

</style>