<template>
    <div>
        <ul>
            <li v-for="(todoItem, index) in propsdata" :key="todoItem.item" class="shadow">
              <i class="checkBtn fa-solid fa-check" :class="{checkBtnCompleted: todoItem.completed}"
                  @click="toggleComplete(todoItem, index)"></i>
                <span :class="{textCompleted : todoItem.completed}"> {{ todoItem.item }}</span>
                <span class="removeBtn" @click="itemRemove(todoItem, index)">  
                  <i class="fa-solid fa-trash"></i>
                </span>
            </li>
        </ul>
    </div>
</template>

<script>
export default {
  props: ['propsdata'],
  /* eslint-disable */
  methods: {
      itemRemove(todoItem, index) {
        localStorage.removeItem(todoItem)
        this.todoItems.splice(index, 1)
        console.log(todoItem, index)
      },
      toggleComplete(todoItem, index) {
        todoItem.completed =! todoItem.completed

        // 로컬 스토리지 데이터 갱신
        localStorage.removeItem(todoItem.item)
        localStorage.setItem(todoItem.item, JSON.stringify(todoItem))
      }
  }
}
</script>

<style scoped>
ul {
  list-style-type: none;
  padding-left: 0px;
  margin-top: 0px;
  text-align: left;
}

li {
  display: flex;
  min-height: 50px;
  height: 50px;
  line-height: 50px;
  margin: 0.5rem 0;
  padding: 0 0.9rem;
  background: white;
  border-radius: 5px;
}
.checkBtn {
  line-height: 45px;
  color: #62acde;
  margin-right: 5px;
}
.checkBtnCompleted {
  color: #b3adad;
}
.textCompleted {
  text-decoration: line-through;
  color: #b3adad;
}
.removeBtn {
  margin-left: auto;
  color: #de4343;
}

</style>