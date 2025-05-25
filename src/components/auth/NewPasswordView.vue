<template>
  <div class="auth-form">
    <h1 class="form-title">Новый пароль</h1>

    <form @submit.prevent="handleSubmit" class="form-container">
      <div class="form-group">
        <MainInput id="newPassword" v-model="newPassword" type="password"  placeholder="новый пароль"/>
        <MainInput id="confirmPassword" v-model="confirmPassword" type="password"  placeholder="повторите пароль"/>
        
      </div>

      <div v-if="message" class="message" :class="{ success: isSuccess, error: !isSuccess }">
        {{ message }}
      </div>

      <MainButton type="submit" :buttonText="'Сохранить'" />
    </form>

    <div class="back-to-login">
      <button @click="switchToLogin" class="back-btn">← Назад к входу</button>
    </div>
  </div>
</template>

<script>
import MainButton from '../ui/MainButton.vue'
import MainInput from '../ui/MainInput.vue'

export default {
components:{
    MainButton,
    MainInput
  },

  name: 'NewPasswordView',
  data() {
    return {
      newPassword: '',
      confirmPassword: '',
      isLoading: false,
      isSuccess: false,
      message: ''
    }
  },
  methods: {
    handleSubmit() {
      if (this.newPassword !== this.confirmPassword) {
        this.message = 'Пароли не совпадают';
        this.isSuccess = false;
        return;
      }

      this.isLoading = true;
      this.message = '';

      // Здесь будет реальный запрос к API
      setTimeout(() => {
        this.isLoading = false;
        this.isSuccess = true;
        this.message = 'Пароль успешно изменён!';
        
        // Автоматический переход через 2 секунды
        setTimeout(() => {
          this.switchToLogin();
        }, 2000);
      }, 1500);
    },
    switchToLogin() {
      this.$emit('switch-to-login');
    }
  }
}
</script>

<style scoped>
/* Стили такие же, как у PasswordResetView */
.auth-form {
  background-color: rgba(172, 172, 172, 0.2);
  backdrop-filter: blur(30px);
  border-radius: 40px;
  width: 600px;
  height: 510px;
  padding: 24px;
  box-shadow: 0 2px 10px rgba(0, 0, 0, 0.1);
  display: flex;
  flex-direction: column;
  justify-content: center;
}


.form-container {
  display: flex;
  flex-direction: column;
  height: 100%; 
  flex-grow: 1;
}

.form-title {
  text-align: center;
  margin-bottom: 48px;
  font-size: 64px;
  color: #FFFF;
}

.form-group {
  width: 100%;
  margin-bottom: 32px;
}

.submit-btn {
  width: 100%;
  padding: 16px 10px;
  background: #4a6cf7;
  color: white;
  border: none;
  border-radius: 80px;
  font-size: 24px;
  cursor: pointer;
  margin-top: 16px;
  transition: background 0.3s;
}

.submit-btn:hover:not(:disabled) {
  background: #3a5bd9;
}

.submit-btn:disabled {
  background: #cccccc;
  cursor: not-allowed;
}

.back-to-login {
  text-align: center;
  margin-top: 32px;
}

.back-btn {
  background: none;
  border: none;
  color: #eaeaea;
  cursor: pointer;
  font-size: 16px;
}

.back-btn:hover {
  color: #4a6cf7;
  text-decoration: underline;
}

.message {
  margin: 16px 0;
  padding: 12px;
  border-radius: 8px;
  text-align: center;
}

.success {
  background-color: rgba(74, 222, 128, 0.2);
  color: #22c55e;
}

.error {
  background-color: rgba(248, 113, 113, 0.2);
  color: #ef4444;
}
</style>