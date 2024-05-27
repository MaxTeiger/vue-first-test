<template>
	<h1>Count : {{ count }}</h1>
	<button @click="count++">+</button>
	<button @click="count--">-</button>
</template>

<script setup>
import { ref } from 'vue';
const count = ref(0);

const props = defineProps(['user']);
</script>

<style scoped>
</style>
