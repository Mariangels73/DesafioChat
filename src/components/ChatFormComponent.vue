<template>
    <form @submit.prevent="handleSubmit" class="chat-form">
      <input type="text" v-model="text" required placeholder="Escribe un mensaje..." />
      <input type="color" v-model="color" />
      <button type="submit">Enviar</button>
    </form>
  </template>
  
  <script>
  export default {
    name: 'ChatFormComponent',
    props: ['user', 'side'],
    data() {
      return {
        text: '',
        color: '#ffffff' // Color inicial blanco
      };
    },
    methods: {
      handleSubmit() {
        const newMessage = {
          text: this.text,
          user: this.user,
          color: this.color // Usar el color seleccionado
        };
        this.$emit('new-message', newMessage);
        this.text = '';
        this.color = '#ffffff'; // Restablecer el color a blanco
      }
    }
  };
  </script>
  
  <style scoped>
  .chat-form {
    display: flex;
    flex-direction: column;
    align-items: center;
    margin-top: 10px;
  }
  
  input[type="text"] {
    max-width: 100%;
    padding: 10px;
    margin-bottom: 10px;
    border: 1px solid #ccc;
    border-radius: 5px;
  }
  
  input[type="color"] {
    width: 40px;
    height: 40px;
    border: none;
    border-radius: 5px;
    margin-bottom: 10px;
  }
  
  button {
    padding: 10px 20px;
    border: none;
    border-radius: 5px;
    background-color: #28a745;
    color: white;
    cursor: pointer;
  }
  
  button:hover {
    background-color: #218838;
  }
  </style>
  