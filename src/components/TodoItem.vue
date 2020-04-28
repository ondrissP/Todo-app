<template>
		<div class="todo-item" :class="{'is-complete':todo.completed}">
			<p>
				<input class="checkbox" type="checkbox" id="checkbox" v-on:change="markComplete" v-bind:checked="todo.completed">
				{{todo.title}}
				<button @click="$emit('del-todo', todo.id)" class="del">x</button>
				</p>
		</div>
</template>

<script>
	export default {
		name: 'TodoItem',
		props: ['todo'],
		methods:{
			markComplete(){
				this.todo.completed = !this.todo.completed
			}
		}
	}
</script>

<style lang="css" scoped>
p{
	width: 100%;
	display: flex;
	align-items: center;
	justify-content: space-between;
}
.is-complete {
	text-decoration: line-through;
}
.todo-item{
	font-size:1.3em;
	padding: .5em;
	color: rgb(216, 216, 216);
	background: linear-gradient(120deg, rgb(4, 0, 80) 0%, rgba(9,9,121,1) 35%, rgba(0,212,255,1) 100%);
	text-shadow: 2px 3px 2px rgb(9,9,121);
	margin-bottom: .5em;
	border-radius: .5em;
	max-width: 80%;
	box-shadow: 5px 5px 4px rgb(9,9,121);
}
.del{
	color: rgb(216, 216, 216);
	font-size: .8em;
	background-color: rgb(211, 39, 39);
	border: rgb(196, 38, 38);
	padding: .3em 1em;
	box-shadow: 3px 3px 4px rgb(90, 90, 90);
	border-radius: 50%;
	cursor: pointer;

}
.del:hover,
.del:focus{
	background-color: rgb(241, 48, 48);
}

</style>