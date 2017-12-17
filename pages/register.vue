<template>
  <v-layout justify-center align-center>
    <v-flex xs12 sm8 md6>
      <v-card class="form" raised>
        <v-form >
          <v-layout column justify-center>
            <v-flex xs12 justify-center align-center>
              <v-card-title justify-center>
                <h1>Register</h1>
              </v-card-title>
            </v-flex>
            <v-flex xs12>
              <v-text-field label="Email" v-model="email" @blur="$v.email.$touch()" :error-messages="errors('email')" type="email">
              </v-text-field>
            </v-flex>
            <v-flex xs12>
              <v-text-field label="Password" v-model="password" @blur="$v.password.$touch()" :error-messages="errors('password')"
                type="password">
              </v-text-field>
            </v-flex>
            <v-flex xs12>
              <v-text-field label="Confirm Password" v-model="confirmPassword" @blur="$v.confirmPassword.$touch()" :error-messages="errors('confirmPassword')"
                type="password">
              </v-text-field>
            </v-flex>
            <v-card-actions>
              <v-btn raised :disabled="$v.$invalid">Register</v-btn>
            </v-card-actions>
          </v-layout>
        </v-form>
      </v-card>
    </v-flex>
  </v-layout>
</template>

<script>
  import { required, minLength, sameAs, email } from 'vuelidate/lib/validators'

  export default {
    data () {
      return {
        email: '',
        password: '',
        confirmPassword: ''
      }
    },
    validations: {
      email: {
        required,
        email
      },
      password: {
        required,
        minLen: minLength(6)
      },
      confirmPassword: {
        required,
        sameAsPassword: sameAs('password')
      }
    },
    methods: {
      errors (value) {
        const errors = []
        if (!this.$v[value].$dirty && !this.$v[value].$error) return
        if (this.$v[value].hasOwnProperty('required')) {
          !this.$v[value].required && errors.push('This filed is required')
        }
        if (value === 'email' && this.$v[value].$error) {
          !this.$v[value].email && errors.push('Provide a valid E-mail address')
        }
        if (value === 'password' && this.$v[value].$error) {
          !this.$v[value].minLen && errors.push('Password must be at least 6 characters long')
        }
        if (value === 'confirmPassword' && this.$v[value].$error) {
          !this.$v[value].sameAsPassword && errors.push('Passwords must be identical')
        }
        return errors
      }
    }
  }
</script>