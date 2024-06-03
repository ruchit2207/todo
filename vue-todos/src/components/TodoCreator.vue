 

<script setup>
import { ref } from 'vue';

const todo = ref('');
const errorMsg = ref('');
const showErrorMsg = ref(false)

const emit = defineEmits(['create-todo']);

const createTodo = () => {
   showErrorMsg.value = false
  console.log('clicked');
  if (todo.value !== '') {
    emit('create-todo', todo.value);
    todo.value=''
  } else {
    showErrorMsg.value = true
    errorMsg.value = 'Todo value cannot be empty!!';
  }
};
</script>

<template>
  <div>
    <div class="input-wrap">
      <input type="text" v-model="todo" />
      <button @click="createTodo">Create</button>
    </div> 
    <p class="err-msg" v-show="showErrorMsg">{{ errorMsg }}</p>
  </div>
</template>

<style scoped lang="scss">
.input-wrap {
  display: flex;
  transition: 250ms ease;
  border: 2px solid #41b080;

  &:focus-within {
    box-shadow: 0 -4px 6px -1px rgb(0 0 0 / 0.1),
      0 -2px 4px -2px rgb(0 0 0 / 0.1);
  }

  input {
    width: 100%;
    padding: 8px 6px;
    border: none;

    &:focus {
      outline: none;
    }
  }

  button {
    padding: 8px 16px;
    border: none;
  }

}
.err-msg {
  margin-top: 6px;
  font-size: 12px;
  text-align: center;
  color: red;
}
</style>
