<template>
  <div class="todoitem" v-if="todoitem[0]">
    <ul>
      <h4>待做</h4>
      <li v-for="(item, index ) in todoitem" v-bind:key="index">
        <span>{{++index}}.</span>
        <b>{{item.con}}</b>

        <div class="btn-box">
          <span @click="complete(index)">完</span>
          <span @click="del(index)">删</span>
        </div>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  data() {
    return {};
  },

  props: {
    todoitem: {
      type: Array,
      required: true
    }
  },
  methods:{
      complete(index){
          console.log(index);
          this.$emit('complete',--index)
      },
      del(index){
        this.$emit("del",--index)
      }
  }


};
</script>

<style scope>
.todoitem li {
  padding: 10px;
  text-align: left;
  color: rgb(45, 114, 102);
  background: rgb(206, 255, 221);
  margin-bottom: 10px;
  overflow: hidden;
}
li b {
  /* display: inline-block; */
  display: -webkit-box;
  width: 60%;
  -webkit-box-orient: vertical;
  -webkit-line-clamp: 1;
  overflow: hidden;
  float: left;
}

li > span:nth-child(1) {
  display: block;
  float: left;
  padding-right: 10px;
  color: rgb(168, 32, 32);
}

.btn-box {
  width: 50px;
  float: right;
}
.btn-box span {
  display: block;
  width: 50%;
  float: left;
  text-align: center;
  padding: 2px 0;
}

.btn-box span:nth-child(1) {
  color: #fff;
  background: rgb(52, 245, 27);
}

.btn-box span:nth-child(2) {
  color: #fff;
  background: red;
  /* text-decoration: line-through rgb(0, 26, 255); */
}
</style>
