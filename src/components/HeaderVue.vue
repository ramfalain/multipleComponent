<template>
    <header>
        <h1>{{title}}</h1>
        <ButtonVue @toggle-add-task="$emit('toggle-add-task')" text="Add Task" color="green"/>
    </header>
</template>

<script>

import ButtonVue from './ButtonVue.vue';

export default {
   name: 'HeaderVue',
   props: {
    title: String,
   
   },
   components: {
    ButtonVue

}

}
</script>

<style scoped>
    header{
        display: flex;
        justify-content: space-between;
        align-items: center;
        margin-bottom: 20px;
    }

    
</style>
