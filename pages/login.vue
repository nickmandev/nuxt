<template>
  <v-layout justify-center align-center>
    <v-flex xs12 sm8 md6>
      <v-card class="form" raised>
        <v-form :model="valid">
          <v-layout column justify-center>
            <v-flex xs12 justify-center align-center>
              <v-card-title justify-center>
                <h1>Login</h1>
              </v-card-title>
            </v-flex>
            <v-flex xs12>
              <v-text-field label="Email" :model="email" type="email" required>
              </v-text-field>
            </v-flex>
            <v-flex xs12>
              <v-text-field label="Password" :model="password" type="password" required>
              </v-text-field>
            </v-flex>
            <v-card-actions>
              <v-btn raised>Login</v-btn>
            </v-card-actions>
          </v-layout>
        </v-form>
      </v-card>
    </v-flex>
  </v-layout>
</template>

<script>
  export default {
    data () {
      return {
        valid: false,
        email: '',
        password: ''
      }
    }
  }
</script>