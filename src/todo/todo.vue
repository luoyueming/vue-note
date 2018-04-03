<template>
	<div class="abc">
		<section class="real-app">
			<input type="text" class="add-input" autofocus="autofocus" placeholder="接下去要做什么?"
			@keyup.enter="adddTodo"
			>
			<Item :todo="todo" v-for="todo in filteredTodos" :key="todo.id" @del="deleteTodo">
			</Item>
			<tabs :filter="filter" :todos="todos" @toggle="toggleFilter" @clearAllCompleted="clearAllCompleted"></tabs>
		</section>
	</div>
</template>

<script>
import Item from './item.vue'
import Tabs from './tabs.vue'
let id = 0
export default {
	data() {
		return {
			todos: [],
			filter: 'all'
		}
	},
	components: {
		Item,
		Tabs
	},
	computed: {
		filteredTodos() {
			if (this.filter === 'all') {
				return this.todos
			}
			const completed = this.filter === 'completed'
			return this.todos.filter(todo => completed === todo.completed)
		}
	},
	methods: {
		adddTodo(e) {
			this.todos.unshift({
				id: id++,
				content: e.target.value.trim(),
				completed: false
			})
			e.target.value = ''
		},
		deleteTodo(id) {
			this.todos.splice(this.todos.findIndex(todo => todo.id === id), 1)
		},
		toggleFilter(state) {
			this.filter = state
		},
		clearAllCompleted() {
			this.todos = this.todos.filter(todo => !todo.completed)
		}
	}
}
</script>

<style lang="stylus" scoped>
	.abc{
		background-color: #ff0;
	}
	.real-app{
		margin 0 auto
		padding-left 10px
		padding-right 10px
		margin-top 20px
	}
	.add-input{
		position: relative;
		left:0;
		top:0
		right:0
		border:none
		height:50px
		display block
		text-indent 30px
		font-size 20px
		border:1px solid #ccc
		width 100%
		display block
	}
</style>
