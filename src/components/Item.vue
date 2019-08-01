<template>
  <li
    :style="{background: bgColor}"
    @mouseenter="handleEnter(true)"
    @mouseleave="handleEnter(false)"
  >
    <label>
      <input type="checkbox" v-model="isCheck" />
      <span>{{todo.title}}</span>
    </label>
    <button class="btn btn-danger" v-show="isShow" @click="deleteItem">删除</button>
  </li>
</template>

<script>
export default {
  props: {
    //属性名/ 属性值的类型
    todo: Object,
    deleteTodo: Function,
    index: Number,
    updateTodo: Function
  },
  data() {
    return {
      bgColor: "white",
      isShow: false
    };
  },
  methods: {
    handleEnter(isEnter) {
      if (isEnter) {
        (this.bgColor = "#ccc"), (this.isShow = true);
      } else {
        (this.bgColor = "white"), (this.isShow = false);
      }
    },
    deleteItem() {
      if (confirm("确定删除吗?")) {
        this.deleteTodo(this.index);
      }
    }
  },
  computed: {
    isCheck: {
      get() {
        return this.todo.complete;
      },

      set(value) {
        this.updateTodo(this.todo, value);
      }
    }
  }
};
</script>

<style scoped>
</style>
