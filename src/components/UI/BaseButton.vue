<template>
    <button :type="type" :class="mode">
        <slot></slot>
    </button>
</template>

<script>
export default {
    props: ['type', 'mode']
}
</script>

<style scoped>
button {
    padding: 0.75rem 1.5rem; font-family: inherit;
    background-color: darkblue; border: none; outline: none;
    color: white; cursor: pointer; font-size: 1em; border-radius: 5px;
}
button:hover, button:active {
    background-color: rgb(2, 2, 56); 
}
.flat {
    background-color: transparent; color: darkmagenta; border: none;
}
.flat:hover, .flat:active {
    background-color: #edd2ff;
}
</style>