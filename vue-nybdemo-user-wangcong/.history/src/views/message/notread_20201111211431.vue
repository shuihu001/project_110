<template>
<div class="notRead">
  {{this.msgList}}
  <!-- <beaTable></beaTable> -->
</div>


</template>

<script>
import beaTable from "../../components/table"
import { getNotLook } from 'network/message.js';
export default {
  name: "notread",
  components:{
    beaTable
  },
  data(){
    return{
      msgList: []
    }
  },
  created(){
    getNotLook(this.$store.getters.token).then(res => {
      this.msgList = res.data
      console.log(res)

    })
  }
}
</script>

<style scoped>
  .notRead{
    background-color: red;
  }
</style>
