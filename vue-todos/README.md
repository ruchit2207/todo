# vue-todos

This template should help get you started developing with Vue 3 in Vite.

## Recommended IDE Setup

[VSCode](https://code.visualstudio.com/) + [Volar](https://marketplace.visualstudio.com/items?itemName=Vue.volar) (and disable Vetur).

## Customize configuration

See [Vite Configuration Reference](https://vitejs.dev/config/).

## Project Setup

```sh
npm install
```

### Compile and Hot-Reload for Development

```sh
npm run dev
```

### Compile and Minify for Production

```sh
npm run build
```


npm init vue@latest
npm i --save-dev uid sass @iconify/vue
<style lang='scss'>
    gooogle fonts-rubik
boilerplate = vbase-3-setup
Vue.js devtools

emit is usedif we want ot send some data from child component to parent component
1. we need to deine emits i child component,fr tht we use 'defineEmits' from 'vue', it accepts n array and inside we can define all the emits tt we need to create

'defineEmits' is going to return a function which,suppose we hv takn it in an variable 'emit', than we call it in an function,and call it with two parameters 

i. name of the emit - 'create-todo'
ii. value tht we need to send - todo.value

now at parent component ,we will create a something to store the data in,now at parent we listen o the custom emitted event from the child component, we write like @create-todo='createTodos',and in tht function we will just push the todo into an array 

while pushing in an array
1. unique id = import {uid} from 'uid'
2.todo
3.isCompleted : null
4.isEditing : null

if we want to pass a props : 
:props_name='props_value'

component receiving it : 
 inside <script> we will inclde 'defineProps' macro,which will either acceptsan array orcan object, the recommended way to define props within view is by using an object,bcoz by using this we can define aditional information about the props like type,required,default value
