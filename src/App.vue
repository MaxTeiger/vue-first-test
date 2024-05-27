<template>
	<HelloWorld :user="user" @update-name="updatedName => displayUpdatedName(updatedName)"/>
	<HelloWorldSlots>
		<p>{{ user.name }}</p>
	</HelloWorldSlots>
	<p>{{ sentence }}</p>
	<form action="">
		<input type="text" v-model="user.name" @change="display">
		<input type="text" v-model="user.age">
	</form>

	<p :class="[user.age > 10 ? 'text-red' : 'text-green']">blabla</p>

	<Counter />
</template>


<script setup>
import HelloWorld from '@/components/HelloWorld.vue';
import HelloWorldSlots from '@/components/HelloWorldSlots.vue';
import Counter from '@/components/Counter.vue';
import { reactive, computed, watch } from 'vue';

const user = reactive({
	name: "Maximilien",
	age: 30
}
);

const name = computed(() => {
	return user.name;
});

const sentence = computed(() => {
	return `Mon nom est ${user.name} et j'ai ${user.age} ${user.age > 1 ? "ans" : "an" }`;
});

const display = () => {
	console.log(user.name, user.age);
}

const displayUpdatedName = (updatedName) => {
	console.log(`From parent component : ${updatedName}`)
}

watch(name, (newValue, oldValue) =>{
	console.log(`New Value: ${newValue}, Old Value: ${oldValue}`);
})

display();

</script>

<style scoped>
.text-red {
	color: indianred;
}

.text-green {
	color: green;
}
</style>
