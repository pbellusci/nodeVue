<template>
  <div>
    <h1> Register </h1>
    <input type="email" v-model="email" name="email" placeholder="Email please" />
    <input type="password" v-model="password" name="password" placeholder=""/>

    <button @click="register">Register</button>
  </div>
</template>

<script>
import AuthenticationService from '@/services/AuthenticationService'
export default {
  name: 'Register',
  data () {
    return {
      email: '',
      password: ''
    }
  },
  watch: {
    email (value) {
      console.log('Email has changed', value)
    }
  },
  mounted () {
    setTimeout(() => {
      this.email = 'Testing mounted'
    }, 1000)
  },
  methods: {
    async register () {
      const response = await AuthenticationService.register({
        email: this.email,
        password: this.password
      })

      console.log(response.data)
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped></style>
