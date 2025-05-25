<template>
  <div class="input-container">
    <input
    :type="type"
      :placeholder="placeholder"
      :required="required"
      :id="id"
      :value="modelValue"
      @input="$emit('update:modelValue', $event.target.value)"
    />
    <div v-if="error" class="error-message">{{ error }}</div>
  </div>
</template>

<script>
export default {
  name: 'MainInput',
  props: {
    type: {
      type: String,
      default: 'text'
    },
    placeholder: {
      type: String,
      default: ''
    },
    required: {
      type: Boolean,
      default: false
    },
    id: {
      type: String,
      default: ''
    },
    error: {
      type: String,
      default: ''
    },
    modelValue: {
      type: [String, Number],
      default: ''
    }
  },
  emits: ['update:modelValue']
}
</script>

<style scoped>
input {
    
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
input:focus {
   border: 2px solid #eaeaea;
   outline: none;
   box-shadow: 0 0 0 2px rgba(74, 108, 247, 0.3);
}
input::placeholder {
  font-family: 'ActayW', sans-serif;
  color: rgba(255, 255, 255, 0.6);
}
</style>