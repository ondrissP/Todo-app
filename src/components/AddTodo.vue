<template>
	<div>
		<form @submit="addTodo">
			<input class="todo-form" type="text" v-model="title" name="title" placeholder="Add Todo..." autofocus>
			<input type="submit" value="Submit" class="btn">
		</form>
	</div>
</template>

<script>
import {v4 as uuidv4 }from "uuid";
	export default {
		name: "AddTodo",
		data() {
			return {
				title: ''
			}
		},
		methods: {
			addTodo(e){
				e.preventDefault();
				const newTodo = {
					id: uuidv4(),
					title: this.title,
					completed: false
				}
				//send up to parent
				if (this.title.length) {
					this.$emit('add-todo', newTodo);
					this.title = '';
				}


			}
		}
	}
</script>

<style scoped>
form{
	display: flex;
	margin: .5em;
}

.todo-form{
	font-size:1.3em;
	flex:10;
	border: rgb(9,9,121) 1px solid;
	border-radius: .5em;
	background: rgb(211, 211, 211);
	box-shadow: 3px 3px 2px rgb(9,9,121);
	text-shadow: 1px 1px 1px rgb(9,9,121);
}
.todo-form:hover,
.todo-form:focus{
	background: rgb(187, 187, 187);
}
.btn{
	font-size:1.3em;
	flex:2;
	background: rgb(211, 211, 211);
	padding: .3em 2em;
	border: black 1px solid;
	border-radius: .5em;
	box-shadow: 3px 3px 2px rgb(9,9,121);
	text-shadow: 1px 1px 1px rgb(9,9,121);
	cursor: pointer;
}
.btn:hover,
.btn:focus{
	background:  rgb(187, 187, 187);
}

</style>