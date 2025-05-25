<template>
    <button class="main-button">
        {{buttonText}}
    </button>
</template>

<script>
import { defineComponent } from 'vue';

export default defineComponent({
    props: {
        buttonText:{
            type: String,
            default: "Кнопка"
        }
    }
});
</script>

<style scoped>
.main-button{
    box-sizing: border-box;
  width: 100%;
  padding: 16px 10px;
  background: #4a6cf7;
  color: white;
  border: none;
  border-radius: 80px;
  font-size: 24px;
  cursor: pointer;
  margin-top: auto;
  margin-bottom: 48px;
  
}

.main-button:hover{
    background: #3a5bd9;
}
</style>