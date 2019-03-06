<template>
  <div class="tabbar">
    <section class="tabBar-wrap">
      <article class="tabBar-box">
        <div class="tabbarcontent">
          <ul class="tabBar-nav" v-if="navList.length > 0">
            <li class="item" v-for="(item, index) in navList"
                @click="selectNavItem(index,item.pagePath)"
                :key="index">
              <p class="item-images">
                <img :src="selectNavIndex === index ? item.selectedIconPath : item.iconPath" alt="iconPath">
              </p>
              <p :class="selectNavIndex === index ? 'item-text item-text-active' : 'item-text' ">
                {{item.text}}
              </p>
            </li>
          </ul>
          <div class="rightleft" style="height: 47px;width: 25%">
            <img src="/static/tabs/share.png" alt="" class="share">
          </div>
        </div>
      </article>
      <!--分享-->
    </section>
  </div>
</template>

<script>
  export default {
    props: ['selectNavIndex', 'needButton', 'handButton', 'btnText'],
    data () {
      return {
        navList: [
          {
            pagePath: "/pages/index/main",
            iconPath: "/static/tabs/home.png",
            selectedIconPath: "/static/tabs/home2.png",
            text: "首页"
          },
          {
            pagePath: "/pages/logs/main",
            iconPath: "/static/tabs/localshop.png",
            selectedIconPath: "/static/tabs/local.png",
            text: "本地中心"
          },
          {
            pagePath: "/pages/mycerter/main",
            iconPath: "/static/tabs/myimg.png",
            selectedIconPath: "/static/tabs/my_active.png",
            text: "我的"
          }
        ],
        selectNavIndex: 0
      }
    },
    methods: {
      selectNavItem(index, pagePath) {
        // console.log(this.selectNavIndex)
        console.log(this.selectNavIndex)

        if (index === this.selectNavIndex) {
          return false;
        }

        if (index == 0 && this.selectNavIndex == -1) {
          this.$emit("fetch-index");
        }
        wx.redirectTo({
          url:pagePath
        })
      },

      /**
       * 路由跳转
       */
      bindNavigateTo(url) {
        wx.navigateTo({
          url
        })
      }
    },
    created () {
    },
    onLoad () {
    }
  }
</script>

<style scoped>
  .tabBar-box {
    position: fixed;
    bottom: 13px;
    width: 100%;
    height: 47px;
    /*border: 1px solid #EBEBEB;*/
    /*background-color: #f8f8f8;*/
  }

  .tabBar-nav {
    width: 70%;
    display: flex;
    background: white;
    border: 1px solid #EBEBEB;
    border-radius: 50px;
    float: left;
    vertical-align: middle;
  }
  .tabbarcontent {
    padding-left: 20px;
    padding-right: 20px;
  }

    .item {
      flex: 1;
      text-align: center;
      padding-top: 8px;
      padding-bottom: 8px;
    }
    .item-text {
      color: #666;
      font-size: 12px;
      transition: .24s linear;
      letter-spacing: 1px;
    }
    .item-text-active {
      color: #FF0038;
    }

    .item-images {
      width: 22px;
      height: 22px;
      margin: 0 auto;
      text-align: center;
      transition: .24s linear;
    }

  .item-images img {
        display: inline;
        width: 100%;
        height: 100%;
      }

    .submit-box-btn {
      position: relative;
      z-index: 999;
      width: 85%;
      height: 90px;
      line-height: 90px;
      border-radius: 10px;
      color: #404040;
      font-size: 36px;
      border: none;
      background-color: #eee;
      text-align: center;
      border: 1px solid #eee;
    }

    .submit-box-btn-active {
      color: #fff;
      border: none;
      border: 1px solid #ff6c00;
      background-color: #ff6c00;
    }

    button {
      border: none;
      outline: none;
    }
  /*分享按钮*/
  .rightleft {
    float: right;
  }
  .share {
    height:49px;
    width: 100%;
    margin-top: 4px;
    vertical-align: middle;
  }
</style>
