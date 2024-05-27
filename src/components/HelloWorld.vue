<template>
	<h1 class="text-red">Hello World</h1>
	<p>Name : {{ props.user.name }}, Age : {{ props.user.age }}</p>
	<p>Name here : {{ name }}</p>
	<input type="text" v-model="name" @input="handleUpdate">
</template>

<script setup>
import { ref } from 'vue';


const emit = defineEmits(["updateName"]);
const name = ref('');

const handleUpdate = (event) => {
	emit('updateName', event.target.value);
}


const props = defineProps(['user']);

</script>

<style scoped>
.text-red {
	color: indianred;
}

.text-green {
	color: green;
}
</style>
