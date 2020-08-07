<template>
    <header>
        <h2>Todo App</h2>
        <div id="nav">
            <router-link to="/">Home</router-link> |
            <router-link to="/about">About</router-link>
        </div>
    </header>
</template>

<script>
export default {
    name: 'Header'
}
</script>

<style scoped>
header {
    background: rgb(19, 18, 18);
    color: white;
    padding: 10px;
    margin-bottom: 1rem;
}

header a {
    text-decoration: none;
}
</style>