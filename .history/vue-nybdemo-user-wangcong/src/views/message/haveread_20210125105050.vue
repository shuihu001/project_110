<template>
<div class="haveRead">
<!-- style="height:100px;width:1000px;background-color: blue;" -->
  <my-table :data1='this.msgList'></my-table>
  <!-- <ul>
    <li >
      <span>标题</span>
      <span >日期</span>
      <span>内容</span>
      </li>
    <li v-for="(item,index) in msgList" :key="index">
      <span class="title">{{item.title}}</span>
      <span class="createTime">{{item.createTime}}</span>
      <span class="content">{{item.content}}</span>
      </li>
  </ul> -->

</div>


</template>

<script>

import { getLooked } from 'network/message.js';
import myTable from "../../components/table/myTable";
export default {
  name: "haveread",
  components : {
    myTable
  },
  data(){
    return{
      msgList: [],

    }
  },
  created(){
    getLooked(this.$store.getters.token).then(res => {
      this.msgList = res.data
      let a = this.msgList.map(item => item.updateTime = item.updateTime.split("T")[0])
      console.log(a)

    })
  }
}
</script>

<style lang='scss' scoped>

</style>
