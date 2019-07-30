<template>
      <div class="todo-header">
        <input type="text" placeholder="请输入你的任务名称，按回车键确认" 
        @keyup.enter="add" v-model="title"/>
      </div>
</template>

<script>
  export default {
    props: {//属性名/属性值的类型/属性的重要性
      addTodo: {
        type: Function,
        required: true
      }
    },
    data () {
      return {
        title: ''
      }
    },
    methods: {
      add () {
        const title = this.title.trim()
        if (!title) {
          alert('请输入')
          return
        }
        const todo = {
          id: Date.now(),
          complete: false,
          title,
        }
        this.addTodo(todo)
        this.title = ''
      }
    }
  }
</script>

<style scoped>

 
</style>
