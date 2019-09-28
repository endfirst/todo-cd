<template>
    
  <div>
      <!-- <button v-on:click='fetchTodoItems'> get all </button> -->
      <ul>
          <!-- <li v-for="(todoItem, index) in todoItems" v-bind:key="index"> -->
              <li v-for="(todoItem, index) in items" v-bind:key="index">
              {{ todoItem }}
              <button v-on:click="removeTodoItem(todoItem, index)">remove</button>
          </li>
      </ul>
  </div>
</template>

<script>
export default {
	props: ['items'],
	// data() {
	// 	return {
	// 		todoItems: [],
	// 	};
	// },
	methods: {
		// fetchTodoItems: function() {
		// 	for (var i = 0; i < localStorage.length; i++) {
		// 		var item = localStorage.key(i);
		// 		this.todoItems.push(item);
		// 	}
		// 	console.log(this.todoItems);
		// },
		removeTodoItem: function(todoItem, index) {
			// this.todoItems.splice(index, 1);
			// this.todoItems.splice(index, 1);
			// localStorage.removeItem(todoItem);
			this.$emit('remove', todoItem, index);
		},
	},
	// created: function() {
	// 	console.log('생성되었음');
	// 	this.fetchTodoItems();
	// },
};
</script>

<style>
</style>