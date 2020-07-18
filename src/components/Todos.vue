<template>
    <div>
        <!-- 把x绑定给TodoItem的属性todo，for x in todos，这里的todos在上一级App.vue里面将被绑定内容 -->
        <!-- 下级TodoItem里面传来的事件del-todo被触发时，将会传给上一级App.vue一个del-todo事件，参数是x的id -->
        <TodoItem 
            v-bind:todo="x" 
            v-bind:key="x.id" 
            v-for="x in todos" 
            @del-todo="$emit('del-todo', x.id)"/>
    </div>
</template>

<script>
import TodoItem from './TodoItem';

export default {
    name: "Todos",
    props: ["todos"],
    components: {
        TodoItem
    }
}
</script>

<style scoped>

</style>