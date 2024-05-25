<template>
  <div id="app">
    <div class="chat-container">
      <div class="user-container left">
        <UserComponent v-if="users.length === 2" :user="users[0]" />
        <ChatFormComponent 
          v-if="users.length === 2" 
          :user="users[0]" 
          @new-message="addMessage" 
          side="left" 
        />
      </div>
      <div class="chat">
        <ChatComponent
          v-if="users.length === 2"
          :messages="messages"
        />
        <p v-else>Loading...</p>
      </div>
      <div class="user-container right">
        <UserComponent v-if="users.length === 2" :user="users[1]" />
        <ChatFormComponent 
          v-if="users.length === 2" 
          :user="users[1]" 
          @new-message="addMessage" 
          side="right" 
        />
      </div>
    </div>
  </div>
</template>

<script>
import axios from 'axios';
import ChatComponent from './components/ChatComponent.vue';
import UserComponent from './components/UserComponent.vue';
import ChatFormComponent from './components/ChatFormComponent.vue';

export default {
  name: 'App',
  components: {
    ChatComponent,
    UserComponent,
    ChatFormComponent
  },
  data() {
    return {
      users: [],
      messages: []
    };
  },
  created() {
    axios.get('https://randomuser.me/api/?results=2')
      .then(response => {
        this.users = response.data.results;
      })
      .catch(error => console.error('Error fetching data:', error));
  },
  methods: {
    addMessage(message) {
      this.messages.push(message);
    }
  }
};
</script>

<style>
#app {
  font-family: Arial, sans-serif;
  text-align: center;
  padding: 20px;
}

.chat-container {
  display: flex;
  justify-content: center;
  align-items: flex-start;
}

.user-container {
  width: 200px; /* Ajusta el ancho de los elementos de usuario según sea necesario */
  text-align: center;
  display: flex;
  flex-direction: column;
  align-items: center;
}

.left {
  margin-right: 10px;
}

.right {
  margin-left: 10px;
}

.chat {
  flex-grow: 1; /* El chat ocupa todo el espacio disponible */
  margin: 0 10px; /* Espaciado entre los usuarios y el chat */
  border: 1px solid #ccc;
  padding: 20px;
  background-color: #f9f9f9;
}
</style>
