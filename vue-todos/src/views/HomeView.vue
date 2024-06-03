<script setup>
import { ref } from "vue";
import { uid } from "uid";
import TodoCreator from "../components/TodoCreator.vue";
import TodoItem from '../components/TodoItem.vue'
import TodoCounter from '../components/TodoCounter.vue'
import { Icon } from "@iconify/vue";

const todoList = ref([]);

console.log('todo-list'+ todoList.value)

 

const setTodoListLocalStorage = ()=>{
  localStorage.setItem('todolist',JSON.stringify(todoList.value))
}

const fetchDataFromLocalStorage = ()=>{
  const savedTodoList = JSON.parse(localStorage.getItem('todolist'))
  console.log(savedTodoList)
  if(savedTodoList){
    todoList.value = savedTodoList
  }
}

fetchDataFromLocalStorage()


const createTodo = (todo) => {
  todoList.value.push({
    id: uid(),
    todo,
    isCompleted: false,
    isEditing: false,
  });
  console.log(todoList.value)
  setTodoListLocalStorage()
};
console.log(todoList.value)

const toggleTodoComplete = (index)=>{
  todoList.value[index].isCompleted != todoList.value[index].isCompleted
  setTodoListLocalStorage()
}

const toggleEditTodo = (index)=>{
  todoList.value[index].isEditing = !todoList.value[index].isEditing
  setTodoListLocalStorage()
}

const updateTodoHandler = (val,index)=>{
  todoList.value[index].todo = val
  setTodoListLocalStorage()
}

const deleteTodoHandler = (todoId)=>{
  todoList.value = todoList.value.filter((todo)=>{
  todo.id !== todoId.id
  })
  setTodoListLocalStorage()
  }

</script>


<template>
  <main>
    <!-- <h1>Create a Todo</h1> -->
    <TodoCreator @create-todo="createTodo" />
     
    <ul class="todo-list" v-if="todoList.length > 0">
      <TodoItem v-for="(item,index) in todoList" v-bind:key="item.id" :todo="item" :index="index" @toggle-complete="toggleTodoComplete" @edit-todo="toggleEditTodo" @update-todo="updateTodoHandler" @delete-todo="deleteTodoHandler"/>
    </ul>
    <p v-else class="todos-msg">
      <Icon icon="noto-v1:sad-but-relieved-face" />
      <span>You have no todo's to complete! Add one!</span>
    </p>
    <TodoCounter/>
  </main>
</template>

<style scoped lang="scss">
main {
  display: flex;
  flex-direction: column;
  max-width: 500px;
  width: 100%;
  margin: 0 auto;
  padding: 40px 16px;

  h1 {
    margin-bottom: 16px;
    text-align: center;
  }
  .todo-list {
    display: flex;
    flex-direction: column;
    list-style: none;
    margin-top: 24px;
    gap: 20px;
  }

  .todos-msg {
    display: flex;
    align-items: center;
    justify-content: center;
    gap: 8px;
    margin-top: 24px;
  }
}
</style>
