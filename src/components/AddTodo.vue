<template>
    <div>
        <form v-on:submit="addTodo">
            <input type="text" name="title" v-model="title" placeholder="Add item">
            <button type="submit" class="button">Add</button>
        </form>
    </div>
</template>

<script>

export default {
    name: 'AddTodo',
    data() {
        return {
            title: ''
        }
    },
    methods: {
        addTodo(e) {
            e.preventDefault()
            const newItem = {
                title: this.title,
                completed: false
            }

            this.$emit('add-todo', newItem)
            this.title = ''
        }
    }
}
</script>

<style scoped>
form {
    display: flex;
    margin-top: 2rem;
    margin-bottom: 5px;
}

input[type=text] {
    flex: 10;
    background: #f1eee9;
    font-family: 'Montserrat', sans-serif;
    font-weight: bold;
    font-size: .9rem;
    padding: 5px;
    border: none;
    border-bottom: 2px solid rgb(66, 64, 64);
}

input[type=text]:focus {
    outline: none;
}

.button {
    flex: 2;
    font-family: 'Montserrat', sans-serif;
    font-weight: bold;
    font-size: .9rem;
    border: none;
    border-radius: 4px;
    background: #3b3ace;
    color: white;
    padding: 8px 16px;
    margin-left: 5px;
    cursor: pointer;
}

.button:hover {
    background: #5151db;
    transition: 200ms ease-in-out;
}
</style>