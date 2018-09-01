<template>
<el-row :gutter="20">
  <el-col :span="12" :offset="6">
    <div class="todo">
      <el-table :data="todos"
        border
        :row-class-name="tableRowClassName">
        <el-table-column prop="id" label="序号" width="50"></el-table-column>
        <el-table-column prop="content" ></el-table-column>
        <!-- <el-table-column prop="status" label="状态" width="50"></el-table-column> -->
        <el-table-column label="操作" width="100">
          <template slot-scope="scope">
            <el-button-group>
              <el-button type="danger" size="mini" @click="toggle(scope.$index)" v-if="scope.row.status" icon="el-icon-circle-close" circle></el-button>
              <el-button type="success" size="mini" @click="toggle(scope.$index)" v-else icon="el-icon-circle-check" circle></el-button>
              <el-button type="danger" size="mini" @click="delTodo(scope.$index)" icon="el-icon-delete" circle></el-button>
            </el-button-group>
          </template>
        </el-table-column>
      </el-table>
      <todo-items :todos="todos" />
    </div>
  </el-col>
</el-row>
</template>

<script>
import TodoItems from '@/components/TodoItem'

export default {
  components: {
    TodoItems
  },
  methods: {
    tableRowClassName ({row, rowIndex}) {
      if (row.status === true) {
        return 'warning-row'
      } else if (rowIndex === false) {
        return 'success-row'
      }
      return ''
    },
    toggle (index) {
      this.todos[index].status = !this.todos[index].status
    },
    delTodo (index, row) {
      this.todos.splice(index)
    }
  },
  data () {
    return {
      newTodo: {autoId: null, content: '', status: false},
      todos: [
        { id: 1, content: 'go to coding', status: true },
        { id: 2, content: 'go to leaning', status: false }
      ]
    }
  }
}
</script>

<style>
  .todo {
    border-radius: 2%;
    border: solid gray 1px;
  }
  .el-table .warning-row {
    background: oldlace;
    text-decoration-line: line-through;
    color: red;
  }

  .el-table .success-row {
    background: #f0f9eb;
    color: green;
  }
</style>
