<template>
    <div>
      <header :style="{height: height + 'px',lineHeight: height + 'px'}">
        <img src="/static/search/logohome.png" alt="" style="width: 91px;height: 19px;">
      </header>
    </div>
</template>

<script>
  export default {
    name: "header",
    data () {
      return {
        height: 0
      }
    },
    onLoad () {
      const _this = this
      wx.getSystemInfo({
        success: (res) => {
          console.log(res)
          _this.height = res.statusBarHeight + 46
        }
      })
    }
  }
</script>

<style scoped>
  header{
    width: 100%;
    background: white;
    position: fixed;
    top: 0px;
    z-index: 999999999999;
  }
  header img{
    position: absolute;
    left: 13px;
    top: 65%;
    margin-top: -9.5px;
  }
</style>
