<script setup>
    import { RouterLink } from 'vue-router';
</script>

<template>
    <nav>
        <img src="../assets/images/Logo.png" alt="Logo">
        <RouterLink class="first" to="/">Home</RouterLink>
        <RouterLink to="/about">Projects</RouterLink>
        <RouterLink to="/about">What's new</RouterLink>
        <RouterLink to="/about">Test</RouterLink>
        <RouterLink to="/about">Link</RouterLink>
        <RouterLink to="/about">About Me</RouterLink>
    </nav>
</template>

<script>

</script>

<style scoped>
nav {
    display: flex;
    flex-wrap: wrap;
    justify-content: left;
}

a {
    color: #686868;
    padding-right: 2rem;
    font-family: Arial, Helvetica, sans-serif;
    font-weight: normal;
    font-size: large;
    text-decoration: none;
}
.first{
    font-weight: bold;
    color: #dddd;
}

img {
    padding: 0 4rem;
}


</style>