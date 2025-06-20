<template>
  <div class="container">
    <div class="form-section">
      <div class="form-wrapper">
        <div class="logo-section">
          <div class="logo-icon">
            <svg class="logo-svg" fill="currentColor" viewBox="0 0 24 24">
              <path d="M7 4V2C7 1.45 7.45 1 8 1H16C16.55 1 17 1.45 17 2V4H20C20.55 4 21 4.45 21 5S20.55 6 20 6H19V19C19 20.1 18.1 21 17 21H7C5.9 21 5 20.1 5 19V6H4C3.45 6 3 5.55 3 5S3.45 4 4 4H7ZM9 3V4H15V3H9ZM7 6V19H17V6H7Z"/>
            </svg>
          </div>
          <div class="logo-text">
            <div class="logo-title">SAFO</div>
            <div class="logo-subtitle">MARKET</div>
          </div>
        </div>

        <div class="welcome-section">
          <h1 class="welcome-title">Xush kelibsiz</h1>
          <p class="welcome-subtitle">Tizimga kirish uchun ma'lumotlaringizni kiriting</p>
        </div>

        <form @submit.prevent="handleLogin" class="login-form">
          <div class="input-wrapper">
            <input
                v-model="loginData.username"
                type="text"
                placeholder="Login ni kiriting"
                class="form-input"
              required
            />
            <User class="input-icon" />
          </div>

          <div class="input-wrapper">
            <input
              v-model="loginData.password"
              :type="showPassword ? 'text' : 'password'"
              placeholder="Parolni kiriting"
              class="form-input password-input"
              required
            />
            <button
              type="button"
              @click="togglePassword"
              class="password-toggle"
            >
              <Eye v-if="!showPassword" class="toggle-icon" />
              <EyeOff v-else class="toggle-icon" />
            </button>
          </div>

          <button type="submit" class="login-button">
            Kirish
          </button>
        </form>

        <div class="signup-section">
          <span class="signup-text">Akkountingiz yo'qmi? </span>
          <a href="#" class="signup-link">Akkount ochish</a>
        </div>
      </div>
    </div>

    <div class="brand-section">
      <div class="brand-content">
        <h2 class="brand-title">SAFO-NON</h2>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref, reactive } from 'vue'
import { User, Eye, EyeOff } from 'lucide-vue-next'

const showPassword = ref(false)
const loginData = reactive({
  username: '',
  password: ''
})


const togglePassword = () => {
  !showPassword.value = showPassword.value
}

const handleLogin = () => {
  if (loginData.username && loginData.password) {
    console.log('Login attempt:', {
      username: loginData.username,
      password: loginData.password
    })
    
    alert(`Kirish urinishi:\nLogin: ${loginData.username}\nParol: ${loginData.password}`)
  }
}



</script>

<style scoped>
* {
  box-sizing: border-box;
}

.container {
  min-height: 100vh;
  display: flex;
  font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, sans-serif;
}

.form-section {
  flex: 1;
  display: flex;
  align-items: center;
  justify-content: center;
  padding: 2rem;
  background-color: white;
}

.form-wrapper {
  width: 100%;
  max-width: 28rem;
  display: flex;
  flex-direction: column;
  gap: 1.5rem;
}

.logo-section {
  display: flex;
  align-items: center;
  gap: 0.75rem;
  margin-bottom: 2rem;
}

.logo-icon {
  width: 4rem;
  height: 4rem;
  background-color: #2563eb;
  border-radius: 0.5rem;
  display: flex;
  align-items: center;
  justify-content: center;
}

.logo-svg {
  width: 2rem;
  height: 2rem;
  color: white;
}

.logo-text {
  display: flex;
  flex-direction: column;
}

.logo-title {
  font-size: 1.125rem;
  font-weight: bold;
  color: #111827;
}

.logo-subtitle {
  font-size: 0.875rem;
  color: #6b7280;
}

.welcome-section {
  display: flex;
  flex-direction: column;
  gap: 0.5rem;
}

.welcome-title {
  font-size: 1.875rem;
  font-weight: bold;
  color: #111827;
  margin: 0;
}

.welcome-subtitle {
  color: #6b7280;
  margin: 0;
}

.login-form {
  display: flex;
  flex-direction: column;
  gap: 1rem;
}

.input-wrapper {
  position: relative;
}

.form-input {
  width: 100%;
  padding: 0.75rem 1rem;
  border: 1px solid #d1d5db;
  border-radius: 0.5rem;
  font-size: 1rem;
  outline: none;
  transition: all 0.2s ease;
}

.form-input:focus {
  border-color: #2563eb;
  box-shadow: 0 0 0 3px rgba(37, 99, 235, 0.1);
}

.password-input {
  padding-right: 3rem;
}

.input-icon {
  position: absolute;
  right: 0.75rem;
  top: 50%;
  transform: translateY(-50%);
  width: 1.25rem;
  height: 1.25rem;
  color: #9ca3af;
}

.password-toggle {
  position: absolute;
  right: 0.75rem;
  top: 50%;
  transform: translateY(-50%);
  background: none;
  border: none;
  cursor: pointer;
  color: #9ca3af;
  transition: color 0.2s ease;
}

.password-toggle:hover {
  color: #6b7280;
}

.toggle-icon {
  width: 1.25rem;
  height: 1.25rem;
}

.login-button {
  width: 100%;
  background-color: #2563eb;
  color: white;
  padding: 0.75rem;
  border-radius: 0.5rem;
  font-weight: 500;
  border: none;
  cursor: pointer;
  transition: background-color 0.2s ease;
  font-size: 1rem;
}

.login-button:hover {
  background-color: #1d4ed8;
}

.login-button:focus {
  outline: none;
  box-shadow: 0 0 0 3px rgba(37, 99, 235, 0.3);
}

.signup-section {
  text-align: center;
}

.signup-text {
  color: #6b7280;
}

.signup-link {
  color: #2563eb;
  font-weight: 500;
  text-decoration: none;
  transition: color 0.2s ease;
}

.signup-link:hover {
  color: #1d4ed8;
}

.brand-section {
  flex: 1;
  background: linear-gradient(135deg, #3b82f6 0%, #8b5cf6 100%);
  display: flex;
  align-items: center;
  justify-content: center;
}

.brand-content {
  text-align: center;
  color: white;
}

.brand-title {
  font-size: 3.75rem;
  font-weight: bold;
  letter-spacing: 0.1em;
  margin: 0;
}

@media (max-width: 768px) {
  .container {
    flex-direction: column;
  }
  
  .form-section {
    padding: 1rem;
  }
  
  .brand-section {
    min-height: 200px;
  }
  
  .brand-title {
    font-size: 2.5rem;
  }
  
  .welcome-title {
    font-size: 1.5rem;
  }
}

@media (max-width: 480px) {
  .form-wrapper {
    max-width: 100%;
  }
  
  .logo-section {
    margin-bottom: 1rem;
  }
  
  .brand-title {
    font-size: 2rem;
  }
}

.fade-enter-active, .fade-leave-active {
  transition: opacity 0.3s ease;
}

.fade-enter-from, .fade-leave-to {
  opacity: 0;
}

.form-input::placeholder {
  color: #9ca3af;
}
</style>





<!-- src/views/Login.vue
<template>
  <div class="container">
    <div class="form-section">
      <div class="form-wrapper">
        <div class="logo-section">
          <div class="logo-icon">
            <svg class="logo-svg" fill="currentColor" viewBox="0 0 24 24">
              <path d="M7 4V2C7 1.45 7.45 1 8 1H16C16.55 1 17 1.45 17 2V4H20C20.55 4 21 4.45 21 5S20.55 6 20 6H19V19C19 20.1 18.1 21 17 21H7C5.9 21 5 20.1 5 19V6H4C3.45 6 3 5.55 3 5S3.45 4 4 4H7ZM9 3V4H15V3H9ZM7 6V19H17V6H7Z"/>
            </svg>
          </div>
          <div class="logo-text">
            <div class="logo-title">SAFO</div>
            <div class="logo-subtitle">MARKET</div>
          </div>
        </div>

        <div class="welcome-section">
          <h1 class="welcome-title">Xush kelibsiz</h1>
          <p class="welcome-subtitle">Tizimga kirish uchun ma'lumotlaringizni kiriting</p>
        </div>

        <form @submit.prevent="handleLogin" class="login-form">
          <div class="input-wrapper">
            <input
              v-model="loginData.username"
              type="text"
              placeholder="Login ni kiriting"
              class="form-input"
              required
            />
            <User class="input-icon" />
          </div>

          <div class="input-wrapper">
            <input
              v-model="loginData.password"
              :type="showPassword ? 'text' : 'password'"
              placeholder="Parolni kiriting"
              class="form-input password-input"
              required
            />
            <button
              type="button"
              @click="togglePassword"
              class="password-toggle"
            >
              <Eye v-if="!showPassword" class="toggle-icon" />
              <EyeOff v-else class="toggle-icon" />
            </button>
          </div>

          <button type="submit" class="login-button">
            Kirish
          </button>
        </form>

        <div class="signup-section">
          <span class="signup-text">Akkountingiz yo'qmi? </span>
          <a href="#" class="signup-link">Akkount ochish</a>
        </div>
      </div>
    </div>

    <div class="brand-section">
      <div class="brand-content">
        <h2 class="brand-title">SAFO-NON</h2>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref, reactive } from 'vue'
import { useRouter } from 'vue-router'
import { User, Eye, EyeOff } from 'lucide-vue-next'

const router = useRouter()
const showPassword = ref(false)
const loginData = reactive({
  username: '',
  password: ''
})

const togglePassword = () => {
  showPassword.value = !showPassword.value
}

const handleLogin = () => {
  if (
    loginData.username === 'admin' &&
    loginData.password === '123456'
  ) {
    router.push('/dashboard')
  } else {
    alert('Login yoki parol noto‘g‘ri!')
  }
}
</script>

<style scoped>
* {
  box-sizing: border-box;
}

.container {
  min-height: 100vh;
  display: flex;
  font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, sans-serif;
}

.form-section {
  flex: 1;
  display: flex;
  align-items: center;
  justify-content: center;
  padding: 2rem;
  background-color: white;
}

.form-wrapper {
  width: 100%;
  max-width: 28rem;
  display: flex;
  flex-direction: column;
  gap: 1.5rem;
}

.logo-section {
  display: flex;
  align-items: center;
  gap: 0.75rem;
  margin-bottom: 2rem;
}

.logo-icon {
  width: 4rem;
  height: 4rem;
  background-color: #2563eb;
  border-radius: 0.5rem;
  display: flex;
  align-items: center;
  justify-content: center;
}

.logo-svg {
  width: 2rem;
  height: 2rem;
  color: white;
}

.logo-text {
  display: flex;
  flex-direction: column;
}

.logo-title {
  font-size: 1.125rem;
  font-weight: bold;
  color: #111827;
}

.logo-subtitle {
  font-size: 0.875rem;
  color: #6b7280;
}

.welcome-section {
  display: flex;
  flex-direction: column;
  gap: 0.5rem;
}

.welcome-title {
  font-size: 1.875rem;
  font-weight: bold;
  color: #111827;
  margin: 0;
}

.welcome-subtitle {
  color: #6b7280;
  margin: 0;
}

.login-form {
  display: flex;
  flex-direction: column;
  gap: 1rem;
}

.input-wrapper {
  position: relative;
}

.form-input {
  width: 100%;
  padding: 0.75rem 1rem;
  border: 1px solid #d1d5db;
  border-radius: 0.5rem;
  font-size: 1rem;
  outline: none;
  transition: all 0.2s ease;
}

.form-input:focus {
  border-color: #2563eb;
  box-shadow: 0 0 0 3px rgba(37, 99, 235, 0.1);
}

.password-input {
  padding-right: 3rem;
}

.input-icon {
  position: absolute;
  right: 0.75rem;
  top: 50%;
  transform: translateY(-50%);
  width: 1.25rem;
  height: 1.25rem;
  color: #9ca3af;
}

.password-toggle {
  position: absolute;
  right: 0.75rem;
  top: 50%;
  transform: translateY(-50%);
  background: none;
  border: none;
  cursor: pointer;
  color: #9ca3af;
  transition: color 0.2s ease;
}

.password-toggle:hover {
  color: #6b7280;
}

.toggle-icon {
  width: 1.25rem;
  height: 1.25rem;
}

.login-button {
  width: 100%;
  background-color: #2563eb;
  color: white;
  padding: 0.75rem;
  border-radius: 0.5rem;
  font-weight: 500;
  border: none;
  cursor: pointer;
  transition: background-color 0.2s ease;
  font-size: 1rem;
}

.login-button:hover {
  background-color: #1d4ed8;
}

.login-button:focus {
  outline: none;
  box-shadow: 0 0 0 3px rgba(37, 99, 235, 0.3);
}

.signup-section {
  text-align: center;
}

.signup-text {
  color: #6b7280;
}

.signup-link {
  color: #2563eb;
  font-weight: 500;
  text-decoration: none;
  transition: color 0.2s ease;
}

.signup-link:hover {
  color: #1d4ed8;
}

.brand-section {
  flex: 1;
  background: linear-gradient(135deg, #3b82f6 0%, #8b5cf6 100%);
  display: flex;
  align-items: center;
  justify-content: center;
}

.brand-content {
  text-align: center;
  color: white;
}

.brand-title {
  font-size: 3.75rem;
  font-weight: bold;
  letter-spacing: 0.1em;
  margin: 0;
}

@media (max-width: 768px) {
  .container {
    flex-direction: column;
  }
  
  .form-section {
    padding: 1rem;
  }
  
  .brand-section {
    min-height: 200px;
  }
  
  .brand-title {
    font-size: 2.5rem;
  }
  
  .welcome-title {
    font-size: 1.5rem;
  }
}

@media (max-width: 480px) {
  .form-wrapper {
    max-width: 100%;
  }
  
  .logo-section {
    margin-bottom: 1rem;
  }
  
  .brand-title {
    font-size: 2rem;
  }
}

.fade-enter-active, .fade-leave-active {
  transition: opacity 0.3s ease;
}

.fade-enter-from, .fade-leave-to {
  opacity: 0;
}

.form-input::placeholder {
  color: #9ca3af;
}

</style> -->
