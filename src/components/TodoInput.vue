<template>
    <div class="inputBox shadow">
        <input class="inputBox" type="text" v-model="newTodoItem" @keyup.enter="addTodo">

        <span class="addContainer" @click="addTodo">
            <i class="fa-solid fa-plus"></i>
        </span>
        
        <!-- <span class="addContainer" @click="delTodo">
            <i class="fa-solid fa-minus"></i>
        </span> -->
    </div>
</template>

<script>
export default {
    data () {
        return {
            newTodoItem: "",
    
        }  
    },
    methods: { 
        /* eslint-disable */
        addTodo() { 
            if (this.newTodoItem !== '') {
            this.$emit('addTodoItem', this.newTodoItem)
            this.clearInput()
            }
        },
        clearInput() {
            this.newTodoItem = ""
        },
        delTodo() {
            window.localStorage.clear();
        }
    }

}
</script>

<style scoped>
input:focus { 
    outline: none !important; border-color: #d6a8e9; box-shadow: 0 0 10px #62EAC6; 
}
.inputBox {
    display: flex;
    background: white;
    width: 100%;
    height: 50px;
    line-height: 50px;
    border-radius: 5px;

}
.inputBox input {
    border-style: none;
    font-size: 0.9rem;
}
.addContainer {
    float: right;
    background: linear-gradient(to right, #6478FB, #8763FB);
    display: block;
    width: 3rem;
    border-radius: 0 5px 5px 0;
}
.addBtn {
    color: white;
    vertical-align: middle;
}

</style>