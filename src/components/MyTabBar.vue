<template>
    <div class="my-tab-bar">
        <div class="tab-item"
        v-for="(item,index) in arr"
        :key="index"
        @click="btn(index,item)"
        :class="{current:index===setIndex}"
            >
        <!-- 图标 -->
        <span class="iconfont" :class="item.iconText"></span>
        <!-- 文字 -->
        <span> {{ item.text }} </span>
    </div>
    </div>
</template>

<script>
export default {
    props:{
        arr:{
            type:Array,
            require:true,
            //自定义校验规则
            validator(value){
                if(value.length>=2&&value.length<=5){
                    return true;
                }
                else{
                    console.error("数据员必须在2-5项");
                    return false;
                }
            }
        }
    },
    data() {
        return {
            setIndex: 0,
        };
    },
    methods:{
        btn(index,obj){
            this.setIndex=index;
            this.$emit('changeName',obj.componentName)
        }
    }
}
</script>

<style lang="less" scoped>
.my-tab-bar {
    position: fixed;
    left: 0;
    bottom: 0;
    width: 100%;
    height: 50px;
    border-top: 1px solid #ccc;
    display: flex;
    justify-content: space-around;
    align-items: center;
    background-color: white;
    .tab-item {
    display: flex;
    flex-direction: column;
    align-items: center;
    }
}
    
.current {
    color: #1d7bff;
}
</style>