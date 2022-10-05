<template>
    <div class="top" :style="{backgroundColor:background,color}">
        {{ title }}
    </div>
</template>

<script>
export default {
    props:{
        background: String, //外部插入此变量的值，必须是字符串类型，否则报错
        color:{
            type: String,//约束color的类型
            default:"#fff"//color默认值(外部不给我color传值，使用默认值)
        },
        title:{
            type: String,
            required:true //必须传入此变量的值
        }
    }
}
</script>

<style scoped lang="less">
    *{
        margin: 0;
        padding: 0;
        list-style: none;
    }
    .top{
        padding: 20px 0;
        width: 100%;
        text-align: center;
        
    }
</style>