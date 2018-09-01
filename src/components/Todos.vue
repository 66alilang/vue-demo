<template>
  <div>
    <div class="container">
      <h2>本周Todos列表</h2>
      <el-row :gutter="20" v-for="(todo, index) in todos" :key="todo.id">
        <el-col :span="6" :offset="6" class="content">
          <div :class="todo.status ? 'todo' : 'undo'">{{index + 1}}:{{todo.content}}</div>
        </el-col>
        <el-col :span="4" >
          <el-button-group>
            <el-button type="danger" size="mini" @click="toggle(index)" v-if="todo.status" icon="el-icon-circle-close" circle></el-button>
            <el-button type="success" size="mini" @click="toggle(index)" v-else icon="el-icon-circle-check" circle></el-button>
            <el-button type="danger" size="mini" @click="delTodo(index)" icon="el-icon-delete" circle></el-button>
          </el-button-group>
        </el-col>
      </el-row>
      <todo-items :todos="todos"/>
    </div>
  </div>
</template>

<script>
import TodoItems from '@/components/TodoItem'
export default {
  components: {
    TodoItems
  },
  data () {
    return {
      todos: [
        { id: 1, content: 'go to coding', status: true },
        { id: 2, content: 'go to leaning', status: false }
      ]
    }
  },
  methods: {
    toggle (index) {
      this.todos[index].status = !this.todos[index].status
    },
    delTodo (index) {
      this.todos.splice(index, 1)
    }
  }
}
</script>

<style>
  li {
    list-style: none;
  }
  .el-row {
    margin-bottom: 1px;
  }
  .el-col {
    border-radius: 4px;
  }
  .container {
    border: rebeccapurple;
    border: solid;
  }
  .undo {
    color: green;
  }
  .todo {
    text-decoration-line: line-through;
    color: brown;
  }
  .content {
    text-align: left;
    font-size: 19px;
  }
</style>
