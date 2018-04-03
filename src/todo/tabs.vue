<template>
	<div class="helper">
		<span class="left">{{unFinishedTodoLength}} 未完成</span>
		<span class="tabs">
			<span v-for="state in states" :key="state" :class="[state, filter === state ? 'actived' : '']" @click="toggleFilter(state)">{{state}} </span>
		</span>
		<span class="clear" @click="clearAllCompleted">清楚完成</span>
	</div>
</template>

<script>
export default {
	props: {
		filter: {
			type: String,
			required: true
		},
		todos: {
			type: Array,
			required: true
		}
	},
	data() {
		return {
			states: ['all', 'active', 'completed']
		}
	},
	computed: {
		unFinishedTodoLength() {
			return this.todos.filter(todo => !todo.completed).length
		}
	},
	methods: {
		clearAllCompleted() {
			this.$emit('clearAllCompleted')
		},
		toggleFilter(state) {
			this.$emit('toggle', state)
		}
	}
}
</script>

<style lang="stylus" scoped>
.left{
	height 50px
	line-height 50px
	text-align center
}
.tabs {
	width 100%
	display flex
	height:50px
}
.tabs span{
	flex 1
	cursor: pointer;
	text-align: center
	line-height 50px

}
.tabs span.actived{
	background blue
	color #fff
}
.clear{
	margin-top 20px
	width 80px
	height: 50px
	display block
	line-height 50px
	margin: auto;
	background: red
	color :#fff
	text-align center
	border-radius 5px
}
</style>
