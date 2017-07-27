<template>
  <div id="app">
    <div class="tbar">
      <div class="wrapper">
        <h1><a href="#"><img src="./assets/img/logo.png" width="18" height="18" alt="DolPic logo"> DolPic</a></h1>
        <ul>
          <li><a href="#search">검색</a></li>
          <li><a href="#">로그인</a></li>
        </ul>
      </div>
    </div>
    <div class="wrapper">
      <router-view></router-view>
      <dolpic-side></dolpic-side>
      <div class="clear"></div>
    </div>
    <dolpic-list></dolpic-list>
  </div>
</template>

<script>
import DolpicSide from './components/DolpicSide.vue'
import DolpicList from './components/DolpicList.vue'

export default {
  name: 'app',
  components: {
    'dolpic-side': DolpicSide,
    'dolpic-list': DolpicList
  }
}
</script>
