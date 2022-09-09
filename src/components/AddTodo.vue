<template>
    <form @submit.prevent="onSubmit">
        <input type="text" v-model="title">
        <button class="btn" type="submit">Create</button>
    </form>
</template>

<script>
export default {
    data() {
        return {
            title: '',
        }
    },

    methods: {
        onSubmit() {
            if(this.title.trim()) {
                const newTodo = {
                    id: Date.now(),
                    title: this.title,
                    completed: false,
                }
                
                this.$emit('add-todo', newTodo)
                this.title = ''
            }
        }
    }   
}
</script>

<style scoped>
form {
    display: flex;
    justify-content:center ;
    padding-top: 20px;
    height: 25px;
    margin-bottom: 10px;
}

input {
    margin-right: 20px;
    width: 400px;
}

.btn {
    width: 75px;
    background-color: rgb(91, 143, 246);
    border: 2px solid #fff;
    color: #fff;
}
</style>