<template>
     <v-app>
    <v-row class="bg-indigo-darken-4 d-sm-flex justify-center" 
    align="center"

    > 
        <v-col cols="10" sm="8">
            <v-container class="bg-grey-lighten-5 pa-5">
                <div class="text-h2 mb-5">User Registration</div>

                <v-text-field
                    placeholder="Username"
                    type="text"
                    v-model="username"
                    label="Username"
                    prepend-inner-icon="mdi-account"
                 
                ></v-text-field>

                <v-text-field
                    placeholder="Email"
                    type="email"
                    v-model="email"
                    label="Email"
                    prepend-inner-icon="mdi-email"
                    :error-messages="errorMessages"
                    @blur="validateEmail"
                
                ></v-text-field>

                <v-text-field
                    placeholder="Password"
                    type="password"
                    v-model="password"
                    label="Password"
                    prepend-inner-icon="mdi-lock"
                  
                ></v-text-field>

                <div class="d-flex justify-center">
                    <v-btn type="submit" color="green" @click="handleRegister" class="mr-2">
                    Register
                    </v-btn>

                    <router-link to="/">
                    <v-btn type="button" color="blue">
                        Login
                    </v-btn>
                    </router-link>
                </div>

                <div class="mt-4 d-flex justify-center">
                    <p v-if="message">{{ message }}</p>
                </div>
                </v-container>
  
        </v-col>
                 
    </v-row>

</v-app>

   
</template>
  
  <script>
  // src/components/Register.vue
import axios from 'axios';

export default {
  data() {
    return {
      username: '',
      email: '',
      password: '',
      message: '',
      errorMessages: []
    };
  },
  methods: {
  validateEmail() {
    const emailPattern = /^[^\s@]+@[^\s@]+\.[^\s@]+$/;
    if (!emailPattern.test(this.email)) {
      this.errorMessages = ['Invalid email format.'];
    } else {
      this.errorMessages = [];
    }
  },
  async handleRegister() {
    // Validate before sending the request
    this.validateEmail();
    if (this.errorMessages.length > 0) {
      return;
    }
    //https://backend-asp-net.vercel.app/api/Registration/login
    //https://localhost:44356/api/Registration/registration
    try {
      const response = await axios.post('https://backend-asp-net.vercel.app/api/Registration/register', {
        Username: this.username,
        Email: this.email,
        Password: this.password,
        isActive: 1
      });
      this.message = response.data;
      this.username = ''
      this.email = ''
      this.password = ''

    } catch (error) {
      this.message = 'Registration failed: ' + (error.response ? error.response.data : error.message);
    }
  }
  }
}

  </script>

<style>


</style>