<template>
    <div class="home" @click="otherClick">
       <div class="wrap" v-for="(item, index) in mainIcon" :key="index">
         <img @dblclick="businessClick(item, index)" @contextmenu.prevent="showSelect(index)" :src="item.img" alt="">
         <p>{{item.name}}</p>
         <div id="openBox" v-if="showOpenindex == index">
           <select-open></select-open>
         </div>
       </div>
        <!-- 业务 -->
      <index-center :index="showOpenindex" :businessName="businessName"></index-center>
      <index-search :index="showOpenindex" :businessName="businessName"></index-search>
      <index-talk :index="showOpenindex" :businessName="businessName"></index-talk>
      <!-- 底部 -->
      <footer-bar @searchText="getSearchText" :index="barIndex" :businessName="businessName"></footer-bar>

      <!-- 渲染搜索字体 -->
      <text-canvas :text='searchText'></text-canvas>
    </div>
</template>
           
<script>
import selectOpen from '@/components/selectOpen'
import indexCenter from '@/views/myCenter/index'
import indexSearch from '@/views/mySearch/index'
import indexTalk from '@/views/myTalk/index'
import footerBar from '@/components/footerBar'
import textCanvas from '@/components/textCanvas'
export default{
  components: {
    selectOpen,
    indexCenter,
    indexSearch,
    indexTalk,
    footerBar,
    textCanvas
  },
  name: 'Home',
  data () {
    return {
      mainIcon:[
        {id: 1, path: '', img: require('../assets/images/1.png'), name: '个人中心'},
        {id: 2, path: '', img: require('../assets/images/2.jpg'), name: '个人引擎'},
        {id: 3, path: '', img: require('../assets/images/3.jpg'), name: '个人对话'}
      ],  
      showOpenindex: null, 
      barIndex: '',
      businessName: '',
      searchText: '',
    }
  },
  methods: {
    businessClick(val, index) {
      this.businessName = val.name;
      this.barIndex = index + '';
    },
    // 显示弹出
    showSelect(val) {
      this.showOpenindex = val;
    },
    // 点击其他区域隐藏当前弹出
    otherClick(e) {
        let box = document.getElementById("openBox");
        if(box){
           if(!box.contains(event.target)){ 
           this.showOpenindex = null;
        }
      }
    },

    //获取搜索框内容
    getSearchText(data) {
      console.log(data,'-------搜索内容');
      this.searchText = data;
    },
  },  
             
}
</script>
<style lang="scss" scoped>
  .home {
    background: linear-gradient(to left,  rgb(146, 140, 140), rgb(48, 63, 68));
    height: 100vh;
    
    .wrap {
      width: 72px;
      position: relative;
      display: inline-block;
      margin: 15px;
      display: flex;
      flex-direction: column;

      img {
        display: inline-block;
        padding: 10px;
        width: 70px;
        height: 70px;
      }

      p {
        width: 70px;
        text-align: center;
        color: #fff;
      }

      &:hover {
          background: rgba(210, 237, 248,.5);
          border: 1px solid rgb(192, 234, 250);
      }
    }
  }       
</style>