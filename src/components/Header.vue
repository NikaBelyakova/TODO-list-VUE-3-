<template>
    <div class="header">
        <div class="container">
            <div class="logo">TODO List</div>
            <div class="form">
                <input type="text" 
                v-model="valueInput" 
                @keypress.enter="addTask">
                <button class="btn" 
                @click="addTask"
                >Add new task</button>
            </div>
        </div>
    </div>

</template>

<script>
    export default {
        data () {
            return {
                valueInput: ''
            }
        },
        methods: {
             addTask () {
                if (this.valueInput === '') { alert ('Заполните поле') };
                this.$emit('add', this.valueInput);
                this.valueInput = '';
            },
        }
    }
</script>

<style scoped>

</style>