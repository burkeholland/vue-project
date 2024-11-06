<template>
  <div class="login">
    <h1>Login</h1>
    <form @submit.prevent="handleLogin">
      <div class="form-group">
        <label for="email">Email:</label>
        <input type="email" id="email" v-model="email" required />
      </div>
      <div class="form-group">
        <label for="password">Password:</label>
        <input type="password" id="password" v-model="password" required />
      </div>
      <button type="submit">Login</button>
    </form>
  </div>
</template>

<script setup>
import { ref, getCurrentInstance } from 'vue'

const email = ref('')
const password = ref('')

const { proxy } = getCurrentInstance()

const handleLogin = async () => {
  try {
    // const response = await fetch('/api/login', {
    //   method: 'POST',
    //   headers: {
    //     'Content-Type': 'application/json',
    //   },
    //   body: JSON.stringify({ email: email.value, password: password.value }),
    // })
    // if (!response.ok) {
    //   throw new Error('Login failed')
    // }
    // const data = await response.json()
    // console.log('Login successful', data)
    proxy.$confetti()
  } catch (error) {
    console.error(error)
  }
}
</script>

<style scoped>
.login {
  max-width: 400px;
  margin: 0 auto;
  padding: 2rem;
  border: 1px solid #ddd;
  border-radius: 8px;
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
  background-color: #fff;
}

.login h1 {
  text-align: center;
  margin-bottom: 2rem;
  font-size: 2rem;
  color: #333;
}

.login .form-group {
  margin-bottom: 1.5rem;
}

.login form label {
  display: block;
  margin-bottom: 0.5rem;
  font-weight: bold;
  color: #555;
}

.login form input {
  width: 100%;
  padding: 0.75rem;
  box-sizing: border-box;
  border: 1px solid #ccc;
  border-radius: 4px;
  font-size: 1rem;
}

.login form button {
  width: 100%;
  padding: 0.75rem;
  background-color: #42b983;
  color: white;
  border: none;
  border-radius: 4px;
  cursor: pointer;
  font-size: 1rem;
  transition: background-color 0.3s ease;
}

.login form button:hover {
  background-color: #369f6b;
}
</style>