<template lang="html">
  <div>
    <div class="header">
      <!--前往我的播放列表-->
      <router-link to="/collection">
        <i class="iconfont icon-menu"></i>
        <!--<i class="iconfont icon-xiangzuo" @click="back" v-if="isBack"></i>-->
      </router-link>
        <p>网易云音乐</p>
        <!--前往正在播放-->
      <router-link to="/playing">
        <i class="iconfont icon-zhengzaibofang" v-if="!playing"></i>
        <img class="gif" src="../../common/img/playing_white.gif" v-if="playing">
      </router-link>
    </div>
  </div>
</template>

<script>
import collection from '../playList/collection.vue'
export default {
  name: 'header_',
//  props: {
//    isBack: {
//      type: Boolean,
//      default: false
//    }
//  },
  computed: {
    playing () {
      return this.$store.state.isPlaying
    },
    playingId() {
      return this.$store.state.playingId
    }
  },
  methods: {
    back () {
      this.$router.back(-1)
    }
  },
  beforeRouteLeave(to, from, next) {
    alert(111);
    if (this.playingId === '') {
      next(false)
    }
  }
}
</script>

<style lang="less">
@import '../../common/css/icon/iconfont.css';
@import '../../common/css/color.less';
.header {
  position: fixed;
  top: 0;
  width: 100%;
  height: 2.5rem;
  padding: 0 1rem;
  line-height: 2.5rem;
  z-index: 10;
  color: #fff;
  box-sizing: border-box;
  display: flex;
  justify-content: space-between;
  background-color: @themeRed;


  .gif {
    width: 17px;
    height: 17px;
  }
}
</style>
