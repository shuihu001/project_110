<template>
<div>
    <Table stripe :columns="columns1" :data="data"  :nextPath="nextPath" @on-row-click="check"></Table>
    </div>
</template>
<script>
    export default {
        name: 'beaTable',
        props:{
            data:{
                type:[],
                default(){
                    return []
                }
            },
            nextPath:{
                type:String,
                default(){
                    return '/'
                }
            },

        },
        data () {
            return {
                columns1: [
                    {
                        title: '展会ID',
                        key: 'id'
                    },
                    {
                        title: '展会名称',
                        key: 'name'
                    },
                    {
                        title: '展会举办方',
                        key: 'hostComp'
                    },
                    {
                        title: '审核状态',
                        key: 'checkState',
                        className: 'check-state'
                    }
                ],
                data1: [
                    {
                        name: 'John Brown',
                        age: 18,
                        address: 'New York No. 1 Lake Park',
                        date: '2016-10-03'
                    },
                    {
                        name: 'Jim Green',
                        age: 24,
                        address: 'London No. 1 Lake Park',
                        date: '2016-10-01'
                    },
                    {
                        name: 'Joe Black',
                        age: 30,
                        address: 'Sydney No. 1 Lake Park',
                        date: '2016-10-02'
                    },
                    {
                        name: 'Jon Snow',
                        age: 26,
                        address: 'Ottawa No. 2 Lake Park',
                        date: '2016-10-04'
                    }
                ]
            }
        },
        methods:{
        check(data){
            console.log(this.nextPath)
         this.$router.push({
           path: this.nextPath,
           query:{
             item: data
         }})
            }
        }
        
    }
</script>

<style scoped>
    .ivu-table td.check-state{
        background-color: #2db7f5;
        color: #fff;
    }
</style>