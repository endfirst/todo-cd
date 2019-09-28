<template>
  <div>
      <input  type="text"  v-model="inputText" v-on:keyup.enter="addTodo">
        <!-- v-on:input="" v-bind:value="" -->
      <button v-on:click="addTodo">add</button>
  </div>
</template>

<script>
export default {
	methods: {
		addTodo: function() {
			var value = this.inputText;
			console.log(value);
			// localStorage.setItem(value, value);
			this.$emit('add', value);
			this.clearInput();
		},
		// addTodo: function(event) {
		// 	// console.log(event);
		// 	if (event.keyCode === 13) {
		// 		console.log('입력');
		// 	}
		// },

		clearInput: function() {
			console.log(this);
			this.inputText = '';
		},
	},
	data: function() {
		return {
			inputText: '',
		};
	},
};
</script>

<style>
</style>