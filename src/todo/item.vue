<template>
	<div :class="['todo-item', todo.completed ? 'completed' : '']">
		<input type="checkbox" class="toggle" v-model="todo.completed" >
		<label  class="b"></label>
		<label class="contail">{{todo.content}}</label>
		<button class="destroy" @click="deleteTodo">X</button>
	</div>
</template>

<script>
export default {
	props: {
		todo: {
			type: Object,
			required: true
		}
	},
	methods: {
		deleteTodo() {
			this.$emit('del', this.todo.id)
		}
	}
}
</script>

<style lang="stylus" scoped>
.todo-item{
	width 100%;
	border-top:1px solid red;
	line-height 50px;
	font-size: 20px;
	background #ccc;
	position relative;
}
.todo-item .toggle{
	position: absolute;
	width: 20px;
	height: 20px;
    opacity: 0;
    left: 10px
	top 15px
	z-index 10

}
.todo-item .b{
	width:20px
	height:20px
	display inline-block
	background red
	position absolute
	left:10px
	top 15px
}
.todo-item button{
	width:20px
	height:20px
	display inline-block
	background red
	position absolute
	right:10px
	top 15px
	border:none
	color #fff
	border-radius 5px
}
.todo-item .contail{
	margin-left 35px
	display block
	color #000
	font-size 16px
	padding-right 20px

}
.completed .b{
	width:20px
	height:20px
	display inline-block
	background green
	position absolute
	left:10px
	top 15px
}
.completed .contail{
	color #aaa
}
</style>
