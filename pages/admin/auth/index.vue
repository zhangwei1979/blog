<template>
  <div class="admin-auth-page">
    <div class="auth-container">
      <form @submit.prevent="onSubmit">
        <AppControlInput type="input" v-model="username">E-Mail Address</AppControlInput>
        <AppControlInput type="password" v-model="password">Password</AppControlInput>
        <AppButton type="submit">{{ isLogin ? 'Login' : 'Sign Up' }}</AppButton>
        <AppButton
          type="button"
          btn-style="inverted"
          style="margin-left: 10px"
          @click="isLogin = !isLogin">Switch to {{ isLogin ? 'Signup' : 'Login' }}</AppButton>
      </form>
    </div>
  </div>
</template>

<script>
import AppControlInput from '@/components/UI/AppControlInput'
import AppButton from '@/components/UI/AppButton'
import axios from 'axios'

export default {
  name: 'AdminAuthPage',
  layout: 'admin',
  components: {
    AppControlInput,
    AppButton
  },
  data() {
    return {
      isLogin: true,
      username: '',
      password: ''
    }
  },
  methods: {
    onSubmit() {
      /*
      let authUrl = 'http://localhost:8080/rest/s1/pop/login'

      if(!this.isLogin) {
        authUrl = 'http://localhost:8080/rest/s1/pop/register'
      }

      axios.post(authUrl, {username:this.username, password:this.password})
        .then(res=>{
          console.log(res)
        })
        .catch(e=>console.error(e))
        */
        this.$store.dispatch('authenticateUser', {isLogin:this.isLogin, username:this.username, password:this.password})
          .then(()=>{
            this.$router.push('/admin')
          })
    }
  }
}
</script>

<style scoped>
.admin-auth-page {
  padding: 20px;
}

.auth-container {
  border: 1px solid #ccc;
  border-radius: 5px;
  box-shadow: 0 2px 2px #ccc;
  width: 300px;
  margin: auto;
  padding: 10px;
  box-sizing: border-box;
}
</style>

