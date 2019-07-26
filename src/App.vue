<template>
	<div id="app">
		<Header v-on:createTodo="createTodo" />
		<Todos v-bind:todos="todos" v-on:removeTodo="removeTodo"/>
	</div>
</template>

<script>
	import Header from '@/components/Header.vue';
	import Todos from '@/components/Todos.vue';

	let todos = [
		{
			id: "1",
			name: "Program",
			done: false
		},
		{
			id: "2",
			name: "SAT Practice",
			done: false
		},
		{
			id: "3",
			name: "Drive",
			done: false
		},
		{
			id: "4",
			name: "Run",
			done: false
		},
		{
			id: "5",
			name: "Party",
			done:false
		}
	];

	export default {
		name: 'app',
		components: {
			Header,
			Todos
		},
		data: function () {
			return {
				todos: todos
			}
		},
		methods: {
			createTodo: function (todo) {
				let todoObject = {
					id: Math.floor(Math.random() * 10000000),
					name: todo,
					done: false
				}

				this.todos.push(todoObject);
			},
			removeTodo: function (id) {
				this.todos = this.todos.filter(todo => todo.id != id)
			}
		}
	}

</script>

<style lang="scss">
body{
	margin: 0;
	padding: 0;
	background-color: #f3f3f3;

	font-family: Arial, Helvetica, sans-serif;
}
</style>
