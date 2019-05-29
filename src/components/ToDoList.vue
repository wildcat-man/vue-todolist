<template>
  <div class="todolist">
    <h2 v-text="title">todolist</h2>

    <input type="text" v-model="newItem">
    <button @click="addNewItem">添加</button>

    <ul>
      <li v-for="(item, ins) in items" :key="ins">
        {{item.id}}
        <span v-text="item.title"></span>

        <button v-on:click="toggleFinish(item)">完成</button>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: "ToDolist",

  data() {
    return {
      title: "my ToDoList.....",
      items: [
        {
          id: 1,
          title: "吃饭"
        },
        {
          id: 2,
          title: "睡觉"
        },
        {
          id: 3,
          title: "学习"
        }
      ]
    };
  },


  methods: {


    toggleFinish(item) {
      this.items.map((itema, index) => {
        if (itema.id === item.id) {
          this.items.splice(item, 1);
        }
      });
      // console.log(item.id);
    },

    addNewItem(){
      this.items.push({
        id:this.id,
        title:this.newItem
        
      })
      console.log(this.newItem);
      this.id++;
      this.newItem = '';
    }


  }

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
  background: #defff0;
  margin: 10px;
  color: rgb(151, 126, 126);
}

a {
  color: #42b983;
}
</style>
