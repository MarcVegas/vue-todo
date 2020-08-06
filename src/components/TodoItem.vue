<template>
    <div class="item" v-bind:class="{'completed':item.completed}">
        <p><input type="checkbox" v-on:change="markComplete"> 
        {{ item.title }} 
        <button v-on:click="$emit('delete-item', item.id)" class="delete">x</button> </p>
    </div>
</template>

<script>
export default {
    name: 'TodoItem',
    props: ["item"],
    methods: {
        markComplete() {
            this.item.completed = !this.item.completed
        }
    }
}
</script>

<style scoped>
.item {
    background: white;
    padding: 1rem;
    font-weight: bold;
    border: 2px solid rgb(197, 195, 195);
    border-radius: 5px;
    margin-bottom: .4rem;
}

.completed {
    text-decoration: line-through;
}

.delete {
    padding: 8px 16px;
    border: none;
    border-radius: 5px;
    cursor: pointer;
    float: right;
    color: rgb(19, 17, 17);
}

.delete:hover {
    background: rgb(211, 36, 36);
    color: white;
    transition: 200ms ease-in-out;
}
</style>