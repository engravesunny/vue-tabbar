<template>
    <div>
        <MyTable :arr="list">
            <template #header> 
                <th>#</th>
                <th>商品名称</th>
                <th>价格</th>
                <th>标签</th>
                <th>操作</th>
            </template>
            <template v-slot:body="scope">
                <td> {{ scope.row.id }} </td>
                <td>{{ scope.row.goods_name }}</td>
                <td>{{ scope.row.goods_price }}</td>
                <td>
                    <input type="text" 
                    class="tag-input form-control"
                    v-if="scope.row.inputVisible"
                    v-focus
                    @blur="scope.row.inputVisible = false"
                    @keydown.enter="enterFn(scope.row)"
                    v-model="scope.row.inputValue"
                    style="width:100px">
                    <button style="display:block" 
                    class="btn btn-primary btn-sm add-tag"
                    v-else
                    @click="scope.row.inputVisible = true"
                    >+Tag</button>
                    <span class="btn btn-primary" style="background:white;color:blue" v-for="(item,index) in scope.row.tags" :key="index">{{ item }}</span>
                </td>
                <td>
                    <button class="btn btn-danger btn-sm" @click="delFn(scope.row.id)">删除</button>
                </td>
            </template>
        </MyTable>
    </div>
</template>

<script>
    import axios from 'axios'
    import MyTable from '@/components/MyTable.vue';
    axios.defaults.baseURL = 'https://www.escook.cn'
export default {
    components:{
        MyTable
    },
    data() {
        return {
            list: [],
        };
    },
    created(){
        axios({
            url:'/api/goods'
        }).then((res)=>{
            console.log(res);
            this.list=res.data.data;
        })
    },
    methods:{
        delFn(id){
            let index = this.list.findIndex(item=>item.id==id);
            this.list.splice(index,1)
            // this.list = this.list.filter(item=>{
            //     item.id!=id
            // })
        },
        enterFn(item){
            if(item.inputValue.trim().length==0)return alert('请输入数据')
            item.tags.push(item.inputValue)
            item.inputValue=''
        }
    },
    
}
</script>

<style>
</style>