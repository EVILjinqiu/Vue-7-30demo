<template>
  <div class="todo-footer">
    <label>
      <input type="checkbox" v-model="checkAll"/>
    </label>
    <span>
      <span>已完成{{completedCount}}</span> / 全部{{todos.length}}
    </span>
    <button class="btn btn-danger" v-if="completedCount>0" @click="deleteCompleted">清除已完成任务</button>
  </div>
</template>

<script type="text/ecmascript-6">
  export default {
    props: {
      todos: Array,
      selectAll: Function,
      deleteCompleted: Function
    },

    computed: {
      completedCount () {
        // console.log('completedCount()')
        return this.todos.reduce((pre, todo) => pre + (todo.complete ? 1 : 0) , 0)
      },

      checkAll: {
        get () {
          // console.log('checkAll get()')
          return this.todos.length === this.completedCount && this.completedCount>0
        },

        set (value) { // 用户点击checkbox时调用
          this.selectAll(value)
        }
      }
    }
  }
</script>

