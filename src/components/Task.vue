<template>
    <div class="Task">
        <div class="text">
            <p v-bind:class="{'done':isDone}">
                {{ text }}
            </p>
            
        </div>
        <div class="buttons">
            <input type="checkbox" @click="this.checkboxHandler">
            <button @click="this.deleteTask(this.index, this.isDone)">Удалить</button>
        </div>
    </div>
</template>

<script>
export default {
    
    props: {
        text: {
            required: true,
            type: String
        },
        index: {
            required: true,
            type: Number
        },
        finishTask: {
            type: Function,
            required: true
        },
        deleteTask: {
            type: Function,
            required: true
        }
    },
    methods: {
        checkboxHandler() {
            this.isDone = !this.isDone;
            this.finishTask(this.isDone);
        },
    },
    data() {
        return {
            isDone: false
        }
        
    },
}
</script>

<style scoped>
    .Task {
        display: flex;
        vertical-align: middle;  
        width: 90%;
        margin: auto;
        margin-top: 20px;
        justify-content: space-between;
        background-color: rgba(253,187,45,1);
        border: 2px solid rgb(173, 126, 23);
        padding: 10px 40px;
        border-radius: 10px;
        align-items: center;
    }
    .text {
        width: 75%;
    }
    p {
        font-size: 1.2em;
        word-wrap: break-word;
    }
    .done {
        text-decoration: line-through;
    }
    input {
        cursor: pointer;
    }
    .buttons {
        display: flex;
        justify-content: space-between;
        height: 100%;
        width: 18%;
    }
    button {
        cursor: pointer;
        display: inline-block;
        padding: 10px 20px;    
        border-radius: 5px;
        background-color: rgba(34,193,195,1);
        color: #fff;
        border: 1px solid rgb(23, 156, 158);
        margin-left: 10px;
        transition: 0.2s;
    }
    button:hover {
        transition: 0.2s;
        transform: scale(110%);
    }
</style>