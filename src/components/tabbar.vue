<template>
  <div class="tabbar">
    <div class="contenttab">
      <ul>
        <li @click="selectNavItem">
          <p>
            <img src="/static/tabs/home.png" alt="">
          </p>
          <p>
            首页
          </p>
        </li>
        <li @click="selectNavItem">
          <p>
            <img src="/static/tabs/home.png" alt="">
          </p>
          <p>
            首页
          </p>
        </li>
        <li @click="selectNavItem">
          <p>
            <img src="/static/tabs/orders.png" alt="">
          </p>
          <p>
            详情
          </p>
        </li>
        <li @click="selectNavItem">

        </li>
      </ul>
    </div>
  </div>
</template>

<script>
  export default {
    data () {
      return {
      }
    },
    methods: {
      selectNavItem () {

      }
    },
    created () {
    }
  }
</script>

<style scoped>
  .tabbar{
    width: 100%;
    height: 45px;
    position: fixed;
    bottom: 20px;
    z-index: 999999999999999999999999;
  }
  .contenttab{
    padding-left: 20px;
    padding-right: 20px;
  }
  .contenttab ul{
    /*background: red;*/
    border-radius: 50px;
    display: flex;
  }
  .contenttab ul li{
    flex: 1;
    text-align: center;
  }
  .contenttab ul li img{
    height: 20px;
    width: 20px;
  }
  .tabbar ul li p{
    font-size: 12px;
  }
</style>
