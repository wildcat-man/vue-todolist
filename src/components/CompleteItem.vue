<template>
  <div class="completeitem" v-if="completeitem[0]">
    <ul>
      <h4>历史记录<span class="del-hist" @click="DelHist">清空</span></h4>
      <li v-for="(item, index) in completeitem" v-bind:key="index">
        <i>{{item.con}}</i>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  data() {
    return {
    };
  },
  methods: {
    DelHist(){
      this.$emit("DelHist");
    }
  },

  props: {
    completeitem: {
      type: Array,
      required: true
    }
  },

};
</script>

<style scope>
.completeitem li {
  padding: 10px;
  text-align: left;
  color: rgb(176, 116, 255);
  background: rgb(224, 224, 224);
  margin-bottom: 10px;
  overflow: hidden;
}
.del-hist{
  display: block;
  float: right;
  font-size: 14px;
  color: rebeccapurple;
}
</style>
