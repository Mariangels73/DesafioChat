<template>
    <div class="user">
      <img :src="user.picture.large" class="avatar" />
      <p class="username">{{ user.name.first }} {{ user.name.last }}</p>
    </div>
  </template>
  
  <script>
  export default {
    name: 'UserComponent',
    props: ['user']
  };
  </script>
  
  <style scoped>
  .user {
    display: flex;
    flex-direction: column;
    align-items: center;
    margin: 10px;
  }
  
  .avatar {
    width: 100px;
    height: 100px;
    border-radius: 50%;
  }
  
  .username {
    font-weight: bold;
    margin-top: 10px;
  }
  </style>
  