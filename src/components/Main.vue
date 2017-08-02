<template>
  <div class='gbox_gallery'>
    <div class='dp_title'>
      <strong onClick='alert($(this).text());'>최신 DolPic</strong>
      <span class='tbox'>더 보기</span>
    </div>
    <div v-for='post in posts' :key='post._id'>
      <div class='gbox' v-bind:style="{ backgroundImage: 'url(' + post.url + ')' }">
        <div class='gbox_thumb' :class="[{g_t_twitter: post.urlType === 1}, {g_t_instagram: post.urlType === 2}, {g_t_facebook: post.urlType === 3}]">
          <div class='gbox_t_title'>{{post.hashTagId.twitterHashTag}}</div>
          <div class='gbox_t_text'>
            <img src='../assets/img/icon_like.png' height='9' alt='like'>{{post.likeCount}}
          </div>
        </div>
      </div>
    </div>
    <div class='clear'></div>
    <div v-for='randomPost in randomPosts' :key='randomPost[0]._id'>
      <div class="dp_title">
        <strong onClick="alert($(this).text());">{{randomPost[0].hashTagId.twitterHashTag}}</strong>
        <span class="tbox">더 보기</span>
      </div>
      <div v-for='value in randomPost' :key="value._id">
        <div class='gbox' v-bind:style="{ backgroundImage: 'url(' + value.url + ')' }">
          <div class='gbox_thumb' :class="[{g_t_twitter: value.urlType === 1}, {g_t_instagram: value.urlType === 2}, {g_t_facebook: value.urlType === 3}]">
            <div class='gbox_t_title'>{{value.hashTagId.twitterHashTag}}</div>
            <div class='gbox_t_text'>
              <img src='../assets/img/icon_like.png' height='9' alt='like'>{{value.likeCount}}
            </div>
          </div>
        </div>
      </div>
    </div>
    <div class='clear'></div>
    <!-- 구글 광고 -->
    <img src='../assets/img/sample_ad2.jpg' width='728' height='90'>
  </div>
</template>

<script>
export default {
  name: 'main',
  data () {
    return {
      active: false,
      posts: [],
      randomPosts: []
    }
  },
  created () {
    this.listNew()
    for (let i = 0; i < 5; i++) {
      this.randomList(i)
    }
  },
  methods: {
    listNew () {
      const apiURL = 'http://dolpic.kr/api/listNew'
      this.$http.post(apiURL).then((result) => {
        console.log(result)
        this.posts = result.data
      })
    },
    randomList (i) {
      const apiURL = 'http://dolpic.kr/api/list'
      this.$http.post(apiURL).then((result) => {
        console.log(result)
        this.randomPosts[i] = result.data
      })
    }
  }
}
</script>
