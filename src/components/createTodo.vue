<template>
    <div class="createTodo">
        <input type="text" v-model="todoDescription">
        <select v-model="selectedPriority">
            <option value="High">High</option>
            <option value="Medium">Medium</option>
            <option value="Low">Low</option>
        </select>
        <button @click="addNew()">Add</button>
    </div>
</template>

<script>
export default {
    name: "CreateTodo",
    props: ['addTodo'],
    data: () => {
        return {
            selectedPriority: 'Medium',
            todoDescription: ''
        }
    },
    methods: {
        addNew: function() {
            this.addTodo(this.todoDescription, this.selectedPriority)
        }
    }
}
</script>

<style>
.createTodo input{
    width: 60%;
    padding: 5px;
    margin: 0 10px;
}

.createTodo select{
    width: 15%;
    padding: 5px;
    margin: 0 10px;
}

.createTodo button{
    width: 15%;
    padding: 5px;
    margin: 0 10px;
}
</style>