<template>
  <div class="m-content">
    <h3>欢迎来到satanaileo的博客</h3>
    <div class="block">
      <el-avatar :size="50" :src="`/icon.jpg`"></el-avatar>
      <div>{{ user.username }}</div>
    </div>
    <div class="maction">
      <el-link href="/blogs">主页</el-link>
      <el-divider direction="vertical"></el-divider>
      <span>
          <el-link type="success" href="/blog/add" :disabled="!hasLogin">发表文章</el-link>
        </span>
      <el-divider direction="vertical"></el-divider>
      <span v-show="!hasLogin">
          <el-link type="primary" href="/login">登录</el-link>
        </span>
      <span v-show="hasLogin">
          <el-link type="danger" @click="logout">退出</el-link>
        </span>
    </div>
  </div>
</template>
<script>

export default {
  name: "Header",
  data() {
    return {
      hasLogin: false,
      user: {
        username: '请先登录',
        avatar: "/icon.jpg"
      },
      blogs: {},
      currentPage: 1,
      total: 0
    }
  },
  methods: {
    logout() {
      const _this = this
      _this.$axios.get('/logout', {
        headers: {
          "Authorization": localStorage.getItem("token")
        }
      }).then((res) => {
        _this.$store.commit('REMOVE_INFO')
        _this.$router.push('/login')
      });
    }
  },
  created() {
    if(this.$store.getters.getUser.username) {
      this.user.username = this.$store.getters.getUser.username
      this.user.avatar = this.$store.getters.getUser.avatar
      this.hasLogin = true
    }
  }
}
</script>