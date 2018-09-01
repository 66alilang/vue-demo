<template>
  <div>
    <el-row class="input">
      <el-col :span="10" :offset="6">
        <el-input v-model.lazy="newTodo.content" placeholder="input you work"></el-input>
      </el-col>
    </el-row>
    <el-row>
      <el-col :span="10" :offset="6">
          <el-button type="primary" size="mini" @click="addTodo">添加</el-button>
          <el-button type="danger" size="mini" @click="reset">重置</el-button>
      </el-col>
    </el-row>
  </div>
</template>

<script>
export default {
  data () {
    return {
      newTodo: {autoId: null, content: '', status: false}
    }
  },
  props: ['todos'],
  methods: {
    addTodo () {
      this.newTodo.id = this.todos.length + 1
      this.todos.push(this.newTodo)
      this.newTodo = {id: null, content: '', status: false}
    },
    reset () {
      this.newTodo = {id: null, content: '', status: false}
    }
  }
}
</script>

<style>
  .input {
    margin: 10px;
  }
</style>
