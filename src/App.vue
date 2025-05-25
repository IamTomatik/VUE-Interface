<template>
  <div id="app" class="min-h-screen bg-gradient-to-br from-blue-50 to-indigo-100 flex items-center justify-center p-4">
    <LoginView
      v-if="currentForm === 'login'"
      @login="handleLogin"
      @switch-to-register="switchToRegister"
      @switch-to-reset="switchToReset"
    />
    <RegisterView
      v-else-if="currentForm === 'register'"
      @register="handleRegister"
      @switch-to-login="switchToLogin"
    />
    <PasswordResetView
      v-else-if="currentForm === 'reset'"
      @switch-to-login="switchToLogin"
      @switch-to-new-password="switchToNewPassword"
    />
    <NewPasswordView
    v-else-if="currentForm === 'new-password'"
    @switch-to-login="switchToLogin"
    />
  </div>
</template>

<script>
import LoginView from "./components/auth/LoginView.vue";
import NewPasswordView from './components/auth/NewPasswordView.vue';
import PasswordResetView from './components/auth/PasswordResetView.vue';
import RegisterView from "./components/auth/RegisterView.vue";


export default {
  name: 'App',
  components: {
    LoginView,
    RegisterView,
    PasswordResetView,
    NewPasswordView
    
  },
  data(){
    return{
        currentForm: 'login'//начальный экран
    }

  },
  methods: {
    handleLogin(credentials) {
      console.log('Login attempt:', credentials);
    },
    switchToRegister() {
      console.log('Switch to register form');
    },
     handleRegister(credentials) {
      console.log('Registration attempt:', credentials);
    },
    switchToRegister() {
      this.currentForm = 'register';
    },
    switchToLogin() {
      this.currentForm = 'login';
    },
    switchToReset() {
      this.currentForm = 'reset';
    },
    switchToNewPassword() {
    this.currentForm = 'new-password';
  }
  }
}
</script>

<style scoped>

/* Можно добавить анимацию перехода */
.v-enter-active,
.v-leave-active {
  transition: opacity 0.3s ease;
}

.v-enter-from,
.v-leave-to {
  opacity: 0;
}
</style>

