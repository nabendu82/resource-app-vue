<template>
    <TheHeader title="Basic Vue App" />
    <the-resources></the-resources>
</template>

<script>
import TheHeader from './components/layouts/TheHeader.vue'
import TheResources from './components/resources/TheResources.vue';

export default {
    components: {
        TheResources,
        TheHeader
    }
}
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Poppins:wght@200;400;600;800&display=swap');

* {
    box-sizing: border-box;
}

html {
    font-family: 'Poppins', sans-serif;
}

body {
    margin: 0;
}
</style>