<template>
  <v-app top-fixed-navbar>
    <header>
      <v-layout class="max-width" row wrap align-center justify-center>
        <v-flex xs-4>
          <v-layout row align-center justify-start>
            <nuxt-link to="/">
              <img class="logo" src="../assets/images/logo.png" alt="Forza Consulting">
            </nuxt-link>
          </v-layout>
        </v-flex>
        <v-flex xs-8 class="links">
          <v-layout row align-center justify-end>
            <nuxt-link v-for="authLink in authLinks" :key="authLink.title" :to="authLink.to">
              <v-icon>mdi-{{ authLink.icon }}</v-icon>
              {{ authLink.title }}
            </nuxt-link>
          </v-layout>
        </v-flex>
      </v-layout>
    </header>
    <v-content class="max-width">
      <nuxt></nuxt>
    </v-content>
  </v-app>
</template>

<script>
  export default {
    data () {
      return {
        authLinks: [{
          icon: 'login',
          title: 'Login',
          to: '/login'
        }, {
          icon: 'account-plus',
          title: 'Register',
          to: '/register'
        }, {
          icon: 'information',
          title: 'About',
          to: '/about'
        }]
      }
    }
  }
</script>