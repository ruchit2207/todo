<script setup>
   import {ref} from 'vue'
   const count = ref(0)
   console.log(count.value)
</script>
<template>
    <div>
        <button @click="count++" >CLICK HERE</button>
        <!-- Notice that we did not need to append .value when using the ref in the template. For convenience, refs are automatically unwrapped when used inside templates  -->
    <p>The valuew of count = {{ count }}</p>
</div>
</template>
 

 

<style lang="scss" scoped>

</style>