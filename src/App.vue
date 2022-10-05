<template>
  <div>
    <MyHeader background="blue" color="white" title="TabBar案例"></MyHeader>
    <div class="main">
      <component :is="comName"></component>
    </div>
    <MyTabBar :arr="tabList" @changeName="changeName"></MyTabBar>
  </div>
</template>

<script>
  import MyHeader from './components/MyHeader.vue';
  import MyTabBar from './components/MyTabBar.vue';
  import MyTable from './components/MyTable.vue';
  import MyGoodsList from './view/MyGoodsList.vue';
  import MyGoodsSearch from './view/MyGoodsSearch.vue';
  import MyUserInfo from './view/MyUserInfo.vue';
export default {
  data() {
    return {
      comName:'MyGoodsList',
      tabList: [
          {
              iconText: "icon-shangpinliebiao",
              text: "商品列表",
              componentName: "MyGoodsList"
          },
          {
              iconText: "icon-sousuo",
              text: "商品搜索",
              componentName: "MyGoodsSearch"
          },
          {
              iconText: "icon-user",
              text: "我的信息",
              componentName: "MyUserInfo"
          }
      ]
    };
  },
  components:{
    MyHeader,
    MyTabBar,
    MyTable,
    MyGoodsList,
    MyGoodsSearch,
    MyUserInfo,
  },
  methods:{
    changeName(cName){
      this.comName = cName
    }
  }
}
</script>

<style lang="less">
  *{
    margin: 0;
    padding: 0;
    list-style: none;
  }
</style>
