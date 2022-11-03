<template>
  <div>
    <h1>每日任务</h1>
    <hr>
    <!-- 使用todo-input组件 -->
    <todo-input @add="onAddNewTask"></todo-input>
    <!-- 使用todo-list组件 -->
    <todo-list :todo="tasklist" class="mt-2" ></todo-list>
    <!-- 使用todo-button组件 -->
    <todo-button v-model:active="activeBtnIndex"></todo-button>
  </div>
</template>

<script>
// 导入TodoList组件
import TodoList from './components/todo-list/TodoList.vue'
// 导入TodoInput组件
import TodoInput from './components/todo-input/TodoInput.vue'
// 导入TodoButton组件
import TodoButton from './components/todo-button/TodoButton.vue'
export default {
  name: 'MyApp',
  data() {
    return {
      todolist: [
      ],
      activeBtnIndex:0,
    }
  },
  components: {
    TodoList,
    TodoInput,
    TodoButton,
  },
  methods: {
    onAddNewTask(taskname) {
      this.todolist.push({
        id: this.todolist.length + 1,
        task: taskname,
        done: false,
      })
    },
  },
  computed:{
    tasklist(){
     switch(this.activeBtnIndex){
       case 0:
         return this.todolist
       case 1:
         return this.todolist.filter(item=>item.done)
       case 2:
         return this.todolist.filter(item=>!item.done)
     }
    }
  }
}
</script>

<style lang="less" scoped></style>
