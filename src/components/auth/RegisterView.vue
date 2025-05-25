
<template>
        <div className = "auth-form">
            <h1 className = "form-title">Регистрация</h1>

            <div className="form-switch">
                <span>Есть аккаунт?</span>
                <button @click="switchToLogin">Войти</button>
            </div>

            <form @submit.prevent="handleSubmit" class="form-container">
                <div class="form-group">
                  <MainInput id="username" v-model="username" type="username"  placeholder="имя"/>
                  <MainInput id="email" v-model="email" type="email"  placeholder="почта"/>
                  <MainInput id="password" v-model="password" type="password"  placeholder="пароль"/>
                </div>
                 <MainButton type="submit" :buttonText="'Зарегистрироваться'" />
            </form>
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
    
  name: 'RegisterView',
  data() {
    return {
        username: '',
        email: '',
        password: ''
    }
  },
  methods: {
    handleSubmit() {
      this.$emit('register', {
        username: this.username,
        email: this.email,
        password: this.password
      })
    },
    switchToLogin() {
      this.$emit('switch-to-login')
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
.form-group input {
    
    box-sizing: border-box;
  width:  100%;
  height: 48px;
  padding: 16px;
  border: 1px solid rgba(255, 255, 255, 0.6);
  border-radius: 80px;
  font-size: 16px;
  margin-top: 16px;
  background-color: rgba(255, 255, 255, 0);
  color:  #eaeaea;
}

.form-group input:focus {
   border: 2px solid #eaeaea;
   outline: none;
   box-shadow: 0 0 0 2px rgba(74, 108, 247, 0.3);
}

.form-group input::placeholder {
  font-family: 'ActayW', sans-serif;
  color: rgba(255, 255, 255, 0.6);
}

</style>