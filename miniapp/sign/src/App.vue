<script>
import {getLocation, getAuth} from './utils/index.js'
export default {
  created () {
    // 用户一打开小程序，就做定位
    getAuth('scope.userLocation', async ()=>{
      let location = await getLocation();
      wx.setStorageSync('location', location)
      console.log('location...', location);
    })
    // 调用登陆获取code
    wx.login({
      success: res=>console.log('res...', res)
    })
  }
}
</script>

<style>
.container {
  height: 100%;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: space-between;
  padding: 200rpx 0;
  box-sizing: border-box;
}
page{
  height: 100%;
}
/* this rule will be remove */
* {
  transition: width 2s;
  -moz-transition: width 2s;
  -webkit-transition: width 2s;
  -o-transition: width 2s;
}
</style>
