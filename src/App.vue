<template>
  <div>
    <todo-header></todo-header>
	<TodoInput v-on:add="addTodoItem"></TodoInput>
	<TodoList v-bind:items="todoItems" v-on:remove="removeTodoItems"></TodoList>
	<TodoFooter v-on:clear="clearTodoItems"></TodoFooter>

  </div>
</template>

<script>
import TodoHeader from './components/TodoHeader.vue';
import TodoFooter from './components/TodoFooter.vue';
import TodoInput from './components/TodoInput.vue';
import TodoList from './components/TodoList.vue';

export default {
	components: {
		//'todo-header': TodoHeader,
		TodoHeader,
		TodoFooter,
		TodoInput,
		TodoList,
	},
	data() {
		return {
			todoItems: [],
		};
	},
	methods: {
		removeTodoItems: function(todoItem, index) {
			this.todoItems.splice(index, 1);
			localStorage.removeItem(todoItem);
		},
		addTodoItem: function(value) {
			this.todoItems.push(value);
			localStorage.setItem(value, value);
		},
		fetchTodoItems: function() {
			for (var i = 0; i < localStorage.length; i++) {
				var item = localStorage.key(i);
				this.todoItems.push(item);
			}
			console.log(this.todoItems);
		},
		clearTodoItems: function() {
			this.todoItems = [];
			localStorage.clear();
		},
	},
	created: function() {
		console.log('생성되었음');
		this.fetchTodoItems();
	},
};
</script>

<style>
</style>