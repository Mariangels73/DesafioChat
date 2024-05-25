<template>
    <div class="messages">
      <MessageComponent
        v-for="(msg, index) in messages"
        :key="index"
        :message="msg"
      />
    </div>
  </template>
  
  <script>
  import MessageComponent from './MessageComponent.vue';
  
  export default {
    name: 'ChatComponent',
    components: {
      MessageComponent
    },
    props: ['messages']
  };
  </script>
  
  <style scoped>
  .messages {
    border: 1px solid #eee;
    max-height: 300px;
    overflow-y: auto;
    padding: 10px;
    background-color: #fff;
  }
  </style>
  