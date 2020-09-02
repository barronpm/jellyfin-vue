<template>
  <v-form @submit="userLogin">
    <v-text-field v-model="login.username" label="Username"></v-text-field>
    <v-text-field v-model="login.password" label="Password"></v-text-field>
    <v-btn block large color="primary" @click="submit">submit</v-btn>
  </v-form>
</template>

<script lang="ts">
export default {
  data() {
    return {
      login: {
        username: '',
        password: ''
      }
    };
  },
  methods: {
    async userLogin() {
      try {
        const response = await this.$auth.loginWith('local', {
          data: this.login
        });
        console.log(response);
      } catch (err) {
        console.log(err);
      }
    }
  }
};
</script>
