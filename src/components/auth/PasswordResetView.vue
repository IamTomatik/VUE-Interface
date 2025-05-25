<template>
  <div class="auth-form">
    <h1 class="form-title">Восстановление пароля</h1>

    <div class="form-switch">
      <span>Вспомнили пароль?</span>
      <button @click="switchToLogin">Войти</button>
    </div>

    <form @submit.prevent="handleSubmit" class="form-container">
      <div class="form-group">
        <MainInput id="email" v-model="email" type="email"  placeholder="ваша почта"/>
      </div>

      <div v-if="message" class="message" :class="{ success: isSuccess, error: !isSuccess }">
        {{ message }}
      </div>

      <MainButton type="submit" :buttonText="'Отправить'" />
    </form>
  </div>
</template>

<script>
import MainInput from '../ui/MainInput.vue'
import MainButton from '../ui/MainButton.vue'
export default {
  components:{
    MainButton,
    MainInput
  },
  name: 'PasswordResetView',
  data() {
    return {
      email: '',
      message: '',
      isSuccess: false
    }
  },
  methods: {
    handleSubmit() {
      console.log('Password reset requested for:', this.email);
      // Имитация успешной отправки
      setTimeout(() => {
        this.isSuccess = true;
        this.message = 'Ссылка для восстановления пароля отправлена на вашу почту';
    
        // Автопереход через 3 секунды (можно убрать, если не нужно)
        setTimeout(() => {
          this.$emit('switch-to-new-password');
        }, 3000);
      }, 1000);
    },
    handleSkip() {
      // Принудительный переход на страницу нового пароля
      this.$emit('switch-to-new-password');
    },
    switchToLogin() {
      this.$emit('switch-to-login');
    }
  }//a@a.ru
}
</script>

<style scoped>

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
}

.form-container {
  display: flex;
  flex-direction: column;
  height: 100%; 
  flex-grow: 1;
}

.form-title {
  text-align: center;
  margin-top: 32px;
  margin-bottom: 16px;
  font-size: 60px;
  color:#FFFF;
}

.form-switch {
  text-align: center;
  margin-bottom: 40px;
  color: #eaeaea;
  font-family: 'Manrope-Regular', sans-serif;
  font-size: 20px;
}

.form-switch button {
  background: none;
  border: none;
  color: #eaeaea;
  cursor: pointer;
  padding: 0 5px;
  font-size: 20px;
}

.form-switch button:hover{
    color: #4a6cf7;
}

.form-group{
    width: 100%;
    box-sizing: border-box;
    
}

.message {
  margin-top: 20px;
  padding: 12px;
  border-radius: 8px;
  text-align: center;
  font-size: 14px;
}

.success {
  background-color: rgba(74, 222, 128, 0.2);
  color: #22c55e;
}

.error {
  background-color: rgba(248, 113, 113, 0.2);
  color: #ef4444;
}

.btn-skip{
    margin-top: 20px;
}
</style>