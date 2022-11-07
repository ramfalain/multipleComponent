<template>
    <div :key="task.id" v-for="task in tasks">
        <TaskVue @delete-task="$emit('delete-task', task.id)" :task="task"/>

    </div>
    
</template>
<script>
import TaskVue from './TaskVue.vue';

export default{
    name: 'TasksVue',

    props: {
        tasks: Array,
    },
    
    components : {
        TaskVue
    },
    emits:['delete-task'],

}
</script>
