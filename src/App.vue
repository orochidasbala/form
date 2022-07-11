<template>
    <SignUP />
</template>

<script>
import SignUP from "./components/SignUp.vue";

export default {
    name: "App",
    components: {
        SignUP,
    },
};
</script>

<style>
#app {
    font-family: Avenir, Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    color: #2c3e50;
    margin-top: 60px;
}
body {
    background-color: #ddd;
    margin: 0;
}
</style>
