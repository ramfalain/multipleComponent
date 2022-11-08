<template>
    <header>
        <h1>{{title}}</h1>
        <ButtonVue @btn-click="$emit('toggle-add-task')" 
        :text="showAddTask? 'close' :'Add Task'" :color="showAddTask ? 'red' : 'green' "/>
    </header>
</template>

<script>

import ButtonVue from './ButtonVue.vue';

export default {
   name: 'HeaderVue',
   props: {
    title: String,
    showAddTask: Boolean,
   
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
