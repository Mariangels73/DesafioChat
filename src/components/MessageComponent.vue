<template>
    <div :class="['message', side]" :style="{ backgroundColor: message.color }">
      <p>{{ message.text }}</p>
      <p class="username">{{ message.user.name.first }} {{ message.user.name.last }}</p>
    </div>
  </template>
  
  <script>
  export default {
    name: 'MessageComponent',
    props: ['message', 'side']
  };
  </script>
  
  <style scoped>
  .message {
    padding: 10px;
    border-radius: 5px;
    margin: 5px 0;
    color: white;
    display: flex;
    flex-direction: column;
  }
  
  .message.left {
    align-self: flex-start;
  }
  
  .message.right {
    align-self: flex-end;
  }
  
  .username {
    font-size: 0.9em;
    margin-top: 5px;
    color: #333;
    text-align: right;
  }
  </style>
  