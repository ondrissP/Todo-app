<template>
	<transition-group  name="bounce">
		<div v-for="todo in todos" :key="todo.id">
			<TodoItem :todo="todo" v-on:del-todo="$emit('del-todo',todo.id)"/>
		</div>
	</transition-group>
</template>

<script>
	import Vue from 'vue'
	import TodoItem from "./TodoItem.vue";

	export default Vue.extend({
		name: 'Todos',
		components: {
			TodoItem
		},
		props: ['todos']
	})
</script>

<style scoped>
.bounce-enter-active {
  animation: bounce-in .5s;
}
.bounce-leave-active {
  animation: bounce-in .5s reverse;
}
@keyframes bounce-in {
  0% {
    transform: scale(0);
  }
  50% {
    transform: scale(1.5);
  }
  100% {
    transform: scale(1);
  }
}
</style>