<template>
    <div>
        <!-- the reason why I dont use $emit right here is because that I want to first construct the todo, then send it, then emit it to the event. -->
        <form @submit.prevent="addTodo"> 
            <input type="text" v-model="title" name="title" placeholder="Add todo...">
            <input type="submit" value="Submit" class="btn">
        </form>
    </div>
</template>

<script>
// import {v4} from 'uuid';

export default {
    name: "AddTodo",
    data() {
        return {
            title: ''
        }
    },
    methods: {
        addTodo() {
            // e.prevetDefault;
            const newTodo = {
                // here we use uuid     -- npm install uuid
                // id: v4(),
                title: this.title,
                completed: false
            };
            // // send up to parent
            this.$emit('add-todo', newTodo);
            this.title = '';
        }
    }
}
</script>

<style scoped>
    form {
        display: flex;
    }

    input[type="text"] {
        flex: 10;
        padding: 5px;
    }

    input[type="submit"] {
        flex: 2;
    }
</style>