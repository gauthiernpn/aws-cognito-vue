<template>
  <v-app>

  <v-toolbar color="primary">
    <i class="material-icons white--text ml-2 ml-4">fingerprint</i>
    <v-toolbar-title class="white--text hidden-xs-only">Auth</v-toolbar-title>
    <v-spacer></v-spacer>
    <v-btn icon @click="navDefault()">
      <v-icon class="white--text">home</v-icon>
    </v-btn>
    <v-toolbar-items class="hidden-xs-only">
      <v-btn v-if="!$store.state.authenticated" class="white--text" @click="navSignIn()" flat>Sign In</v-btn>
      <v-btn v-if="!$store.state.authenticated" class="white--text mr-4" @click="navRegister()" flat>Register</v-btn>
      <v-btn v-if="$store.state.authenticated" class="white--text mr-4" @click="navSignOut()" flat>SignOut</v-btn>
    </v-toolbar-items>
    <v-menu bottom left class="hidden-sm-and-up">
      <v-btn icon slot="activator" >
        <v-icon class="white--text">more_vert</v-icon>
      </v-btn>
      <v-list>
        <v-list-tile
          v-if="!$store.state.authenticated"
          @click="navSignIn()">
          <v-list-tile-title >
            Sign In
          </v-list-tile-title>
        </v-list-tile>
        <v-list-tile
          v-if="!$store.state.authenticated"
          @click="navRegister()">
          <v-list-tile-title>
            Register
          </v-list-tile-title>
        </v-list-tile>
        <v-list-tile
          v-if="$store.state.authenticated"
          @click="navSignOut()">
          <v-list-tile-title>
            Sign Out
          </v-list-tile-title>
        </v-list-tile>
      </v-list>
    </v-menu>
  </v-toolbar>

  <v-content>
    <router-view></router-view>
  </v-content>

  <v-footer fixed app>
    <v-layout column align-center justify-center>
      <div class="ml-3">
        <span>&copy; 2018 <a href="http://sonabstudios.com">SonabStudios&trade;</a> is a trademark of Jayson Nabor</span>
      </div>
    </v-layout>
  </v-footer>

  </v-app>
</template>

<script>
import router from '../routes'

export default {
  methods: {
    navDefault: function () {
      console.log('navigating to sign in')
      router.push('/home')
    },
    navSignIn: function () {
      console.log('navigating to sign in')
      router.push('/signin')
    },
    navRegister: function () {
      console.log('navigatig to sign up')
      router.push('/register')
    },
    navSignOut: function () {
      console.log('signing out')
      this.$store.state.authenticated = false
      router.push('/home')
    }
  }
}
</script>

<style>
.main-card {
  max-width: 1000px;
}
</style>
