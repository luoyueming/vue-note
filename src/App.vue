<template>
  <div id="app">
    <div id="cover">
    </div>
    <Header>
    </Header>
    <Todo>
    </Todo>
    <Footer>
    </Footer>
  </div>
</template>

<script>
import Header from './todo/header.vue'
import Footer from './todo/footer.vue'
import Todo from './todo/todo.vue'
export default {
    components: {
      Header,
      Footer,
      Todo
    }
  }
</script>

<style lang="stylus" scoped>
body{
  background-color yellow
}
#app{
  position absolute
  left 0
  top 0
  right 0
  bottom 0
  height: 100%
  background-color yellow
}
#cover{
  position absolute
  left 0
  top 0
  bottom 0
  right 0
  background-color yellow
  opacity .9
  z-index -1
  height: 100%
}
</style>
