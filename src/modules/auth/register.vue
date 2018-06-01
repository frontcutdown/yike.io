<template>
  <div class="row pt-3">
    <div class="offset-sm-4 col-sm-4">
      <div class="box">
        <h4 class="text-center font-weight-normal mt-2">用户注册</h4>
        <div class="box-body">
          <form @submit.prevent="submit">
            <div class="form-group input-group-lg">
              <label>邮箱地址</label>
              <input type="text" class="form-control" placeholder="example@yike.io" v-model="email">
            </div>
            <div class="form-group input-group-lg">
              <label>用户名</label>
              <input type="text" class="form-control" placeholder="" v-model="username">
            </div>
            <div class="form-group input-group-lg">
              <label>密码</label>
              <input type="password" class="form-control" placeholder="" v-model="password">
            </div>
            <button type="submit" class="my-2 btn btn-primary w-100 btn-lg">注册</button>
          </form>
        </div>
      </div>
    </div>
    <div class="offset-sm-3 col-sm-6 text-center mt-2">
      <p>已有账号？ <router-link class="text-blue" :to="{ name: 'auth.login' }">快速登录</router-link></p>
    </div>
  </div>
</template>

<script>
  import { mapActions } from 'vuex'
  import GooglePlus from '@icons/google-plus'
  import FacebookIcon from '@icons/facebook'
  import QqIcon from '@icons/qqchat'
  import GithubIcon from '@icons/github-circle'

  export default {
    components: {GooglePlus, FacebookIcon, QqIcon, GithubIcon},
    data() {
      return {
        username: '',
        email: '',
        password: '',
      }
    },
    methods: {
      ...mapActions(['attemptRegister']),

      async submit() {
        const { username, email, password } = this

        this.attemptRegister({ username, email, password })

        this.$router.push({ name: 'home' })
      }
    }
  }
</script>