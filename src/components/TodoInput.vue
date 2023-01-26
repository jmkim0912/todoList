<template>
    <div class="inputBox shadow">
        <input class="inputBox" type="text" v-model="newTodoItem" @keyup.enter="addTodo">
        
        <span class="addContainer" @click="addTodo">
            <i class="fa-solid fa-plus"></i>
        </span>
        
        <AlertModal v-if="showModal" @close="showModal = flase">
          <h3 slot=header>
            경고!!    
            <i class="fa-sharp fa-solid fa-circle-xmark" @click="showModal = false"></i>
          </h3>

          <h3 slot=body>
            값을 입력해주세요
          </h3>
        </AlertModal>
    </div>
</template>

<script>
/* eslint-disable */
import AlertModal from './common/Modal.vue'

export default {
    data () {
        return {
            newTodoItem: "",
            showModal: false
        }  
    },
    methods: { 
        /* eslint-disable */
        addTodo() { 
            if ( this.newTodoItem !== '') {
            this.$emit('addTodoItem', this.newTodoItem)
            this.clearInput()
            } else {
              this.showModal =! this.showModal
            }
        },
        clearInput() {
            this.newTodoItem = ''
        },
        delTodo() {
            window.localStorage.clear();
        },
    },
    components: {
      AlertModal
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
.closeModalBtn {
  color: #42b983;
}

</style>