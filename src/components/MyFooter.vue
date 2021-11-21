<template>
  <div class="todo-footer" v-show="total">
    <label>
      <input type="checkbox" :checked="isAll" @change="changeAll"/>
    </label>
    <span> <span>已完成{{doneTotal}}</span> /全部{{total}} </span>
    <button class="btn btn-danger" @click="clearAll">清除已完成任务</button>
  </div>
</template>
<script>
export default {
  name: "MyFooter",
  props:['todos','checkAllTodo','clearAllTodo'],
  computed:{
    total(){
      return this.todos.length;
    },
    isAll(){
      return this.doneTotal===this.total && this.total>0
    },
    doneTotal(){
      let i=0;
      this.todos.forEach(todo => {
        if(todo.done){i++}
      });
      return i;
    }
  },
  methods:{
    changeAll(e){
      this.checkAllTodo(e.target.checked)
    },
    clearAll(){
      this.clearAllTodo()
    }
  }
};
</script>

<style scoped>
.todo-footer i{
height: 40px;
line-height: 40px;
padding-left: 6рх;
margin-top: 5px;}
.todo-footer label {
display: inline-block;
margin-right: 20px;
cursor: pointer;}
.todo-footer label input {
position: relative ;
top: -1px;
vertical-align: middle;
margin-right: 5px;}
.todo-footer button{
float: right;
margin-top: 5px;}
</style>