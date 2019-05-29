<template>
  <div class="todo">
    <h1>{{ msg }}</h1>

    <input type="text" v-model="inputValue">
    <button v-on:click="handleBtn">提交</button>

    <ToDoItem v-bind:todoitem="todoitem" @complete="complete" @del="del"/>
    <CompleteItem v-bind:completeitem='completeitem' @DelHist="DelHist"/>
  </div>
</template>

<script>
import ToDoItem from "./ToDoItem";
import CompleteItem from "./CompleteItem";

export default {
  name: "todolsit",
  data() {
    return {
      msg: "Todolist",
      inputValue: "",
      todoitem: [
        {con:"学习前端"},
        {con:"学习全栈"},
        {con:"学习vue"},
      ],
      completeitem: [],
    };
  },
  components: {
    ToDoItem,
    CompleteItem
  },

  methods: {
    // 添加列表
    handleBtn() {
      if (this.inputValue) {
        this.todoitem.push({ con: this.inputValue });
        this.inputValue = "";
      }
    },

    // 点完成按钮-添加到历史记录
    complete(ind) {
      this.completeitem.push(this.todoitem[ind]);
      this.todoitem.splice(ind, 1);
    },

    // 删除待做
    del(ind){
      console.log(ind);
      this.todoitem.splice(ind, 1);
    },

    // 清空历史
    DelHist(){
      this.completeitem=[]
    }
  },

};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h1,
h2 {
  font-weight: normal;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  margin: 0 10px;
}

a {
  color: #42b983;
}
</style>
