<template>
  <div>
      <input type="text" class="todo-input" placeholder="What needs to be done.." @keyup.enter="addTodo" v-model="newTodo">
      <div v-for="todo in todos" :key="todo.id" class="todo-item">
          {{todo.title}}
      </div>
      
  </div>
</template>

<script>
import { METHODS } from 'http';
export default {
  name: 'todo-list',
  data(){
      return{
          newTodo: '',
          idForTodo: 3,
          todos:[
              {
                'id': 1,
                'title':'New todo title',
                'completed': false,
              },
              {
                'id': 2,
                'title':'second todo title',
                'completed': false,
              }
          ]
      }
  },
  methods:{
      addTodo(){
          if(this.newTodo.trim().length == 0){
              return
          }
          this.todos.push({
              id:this.idForTodo,
              title:this.newTodo,
              completed: false,
          })
          this.newTodo = ''
          this.idForTodo++

      }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang="scss">
.todo-input {
    width:100%;
    padding:10px 18px;
    font-size: 18px;
    margin-bottom: 16px;
    border-radius: 3px;
    border: 1px solid #ccc;
}

</style>
