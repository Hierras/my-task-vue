<template>
  <div class="AddTask">
    <div><input v-model="inputText" type="text" placeholder="Название дела..."></div>
    <div><button @click="addTask(inputText)">Добавить</button></div>
  </div>
</template>

<script>
export default {
    data () {
        return {
            inputText: ''
        }
    },
    props: {
        addTask: {
            type: Function,
            required: true
        }
    }
}
</script>

<style scoped>
    .AddTask {
        display: flex;
        margin: auto;
        margin-top: 20px;
        justify-content: center;
    }
    input {
        display: inline-block;
        width: 500px;
        padding: 15px;
        border-radius: 10px;
        border: 0px;
        border-bottom: 4px solid rgba(34,193,195,1);
        outline: none;
        color: #404040;
    }
    button {
        cursor: pointer;
        display: inline-block;
        padding: 15px;
        border-radius: 10px;
        background-color: rgba(253,187,45,1);
        color: #fff;
        border: 1px solid rgb(173, 126, 23);
        border-bottom: 4px solid rgb(173, 126, 23);
        margin-left: 10px;
        transition: 0.2s;
    }
    button:hover {
        transition: 0.2s;
        border: 1px solid rgb(173, 126, 23);
        transform: translateY(4px);
    }

</style>