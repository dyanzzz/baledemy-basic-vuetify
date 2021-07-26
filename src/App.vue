<template>
  <v-app>
    <v-container>
      <v-card tile elevation="1" class="mt-5">
        <v-card-title>
          <h1>Login</h1>
        </v-card-title>

        <v-form @submit.prevent="handleSubmit" v-model="isValid">
          <v-card-text>
            <v-text-field label="Email" prepend-icon="mdi-account-circle" 
              :rules="emailRules"
              v-model="user.email" />
            <v-text-field label="Password" prepend-icon="mdi-lock" 
              :append-icon="showPassword ? 'mdi-eye' : 'mdi-eye-off'" 
              :type="showPassword ? 'text' : 'password'" 
              :rules="passwordRules"
              @click:append="handleToggle"
              v-model="user.password" />
          </v-card-text>
          
          <v-divider></v-divider>

          <v-card-actions>
            <v-btn color="success" type="submit" :disabled="!isValid">Login</v-btn>
            <v-btn color="info">Register</v-btn>
          </v-card-actions>
        </v-form>

      </v-card>
    </v-container>
  </v-app>
</template>

<script>


export default {
  name: 'App',

  components: {
    
  },

  data() {
    return {
      showPassword: false,
      user: {
        email: '',
        password: ''
      },
      isValid: false, // melakukan pengecekan pada form, jika form sudah siap atau belum untuk disubmit
      emailRules: [ // config validasi vuetify
        v => !!v || 'Email is required',
        v => /.+@.+\..+/.test(v) || 'E-mail must be valid',
      ],
      passwordRules: [ // config validasi vuetify
        v => !!v || 'Password is required',
        v => (v && v.length <= 10) || 'Password must be less than 10 characters',
      ]
    }
  },

  methods: {
    handleToggle() {
      this.showPassword = !this.showPassword
    },
    handleSubmit() {
      console.log(this.user)
      this.user = {
        email: '',
        password: ''
      }
    }
  }
};
</script>
