<template>
    <v-app class="v-app">
    <v-row class="bg-indigo-darken-4 d-sm-flex justify-center" 
    align="center"

    > 
        <v-col cols="10" sm="8">
                <v-container class="bg-grey-lighten-5">
                    
                    <div class="text-h2 mb-5">User Login</div>
                    
                        <v-text-field
                        placeholder="Email"
                        type="email"
                        v-model="email"
                        required="true"
                        label="Email"
                        prepend-inner-icon="mdi-email"
                        :error-messages="errorMessages"
                        @blur="validateEmail"
                        >

                        </v-text-field>
                        <v-text-field
                        placeholder="Password"
                        type="password"
                        v-model="password"
                        required="true"
                        label="Password"
                        prepend-inner-icon="mdi-lock"
                        >

                        </v-text-field>
                        <div class="d-flex justify-center">
                            <v-btn  color="blue" @click="handleLogin">
                                Login
                            </v-btn>

                            <router-link to="/register">
                            <v-btn class="ml-1" type="submit" color="green">
                                Register
                            </v-btn>
                            </router-link>

                        </div>
                        <div class="d-flex mt-4 justify-center">
                                <p v-if="message">{{ message }}</p>
                        </div>
                </v-container>
            </v-col>
                 
    </v-row>

</v-app>

</template>


<!-- <script setup>
import { ref, computed } from 'vue';

const email = ref('');
const errorMessages = ref([]);

function validateEmail() {
  errorMessages.value = [];
  
  if (!email.value) {
    errorMessages.value.push('Email is required');
  } else if (!/.+@.+\..+/.test(email.value)) {
    errorMessages.value.push('Email must be valid');
  }
}

</script> -->

  
<script>
 // src/components/Login.vue
 // src/components/Login.vue
import axios from 'axios';

export default {
  data() {
    return {
      email: '',
      password: '',
      message: ''
    };
  },
  methods: {
    async handleLogin() {
      try {
        const response = await axios.post('https://localhost:44356/api/Registration/login', {
          Email: this.email,
          Password: this.password,
          isActive: 1
        });
        this.message = response.data;

        this.email = ''
        this.password = ''

      } catch (error) {
        if (error.response) {
          // Server responded with a status other than 2xx
          this.message = `Login failed: ${error.response.data}`;
        } else if (error.request) {
          // Request was made but no response received
          this.message = 'Login failed: No response from server';
        } else {
          // Something else happened in setting up the request
          this.message = `Login failed: ${error.message}`;
        }
      }
    }
  }
};

  </script>
  


<style scoped>


.v-app {
  height: 100%;
 background-color: green;
}

</style>