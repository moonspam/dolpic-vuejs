<template>
  <div class="gbox_side">
    <ul class="hot_box">
      <li class="title">오늘의 핫돌픽</li>
      <li v-for='rank in ranks' v-bind:key='rank._id'>
        <a href="#">{{rank.twitterHashTag}}</a> <span>{{rank.likeCount}} <img src="../assets/img/icon_like.png" height="16"></span>
      </li>
    </ul>
    <!-- 구글 광고 -->
    <img src="../assets/img/sample_ad.jpg" width="300" height="600">
    <a href="https://play.google.com/store/apps/details?id=com.tony.mocadev.dolpicapp" target="_blank"><img src="../assets/img/banner_300_150923.jpg" width="300" height="250"></a>
    <!-- 공지사항 -->
    <a class="twitter-timeline" href="https://twitter.com/iluku" data-widget-id="361469113698222080"></a>
    <div class="copyright">&copy; 2015 DolPic | <a href="#">Feedback</a></div>
  </div>
</template>

<script>
export default {
  name: 'dolpic-side',
  data () {
    return {
      active: false,
      ranks: []
    }
  },
  created () {
    this.rankList()
  },
  methods: {
    rankList () {
      const apiURL = 'http://dolpic.kr/api/hotdolpics'
      this.$http.post(apiURL).then((result) => {
        console.log(result)
        this.ranks = result.data
      })
    }
  }
}
</script>

