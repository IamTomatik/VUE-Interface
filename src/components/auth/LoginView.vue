
<template>
        <div class = "auth-form">
            <h1 class = "form-title">Вход</h1>

            <div class="form-switch">
                <span>Нет аккаунта?</span>
                <button @click="switchToRegister">Регистрация</button>
            </div>

            <form @submit.prevent="handleSubmit" class="form-container">
                <div class="form-group">
                    <MainInput id="email" v-model="email" type="email"  placeholder="почта"/>
                    <MainInput id="password" v-model="password" type="password"  placeholder="пароль"/>
                </div>

                <div class="forgot-password">
                    <button type="button" @click="switchToReset">Забыли пароль</button>
                </div>

              <MainButton type="submit" :buttonText="'Войти'" />
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
  name: 'LoginView',
  data() {
    return {
      email: '',
      password: ''
    }
  },
  methods: {
    handleSubmit() {
      this.$emit('login', {
        email: this.email,
        password: this.password
      })
    },
    switchToRegister() {
      this.$emit('switch-to-register')
    },
    switchToReset() {
      this.$emit('switch-to-reset');
    }
  }
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
  font-size: 64px;
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

.forgot-password {
  text-align: right;
  margin-top: 10px;
}

.forgot-password button {
  background: none;
  border: none;
  color: #eaeaea;
  cursor: pointer;
  font-size: 14px;
  padding: 0;
}

.forgot-password button:hover {
  color: #4a6cf7;
  text-decoration: underline;
}
</style>