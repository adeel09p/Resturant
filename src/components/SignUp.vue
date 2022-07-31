<!-- eslint-disable no-unused-vars -->
<!-- eslint-disable vue/multi-word-component-names -->
<template>
  <h1>Sign Up</h1>
  <div class="register">
    <input type="text" v-model="name" placeholder="Enter Name" />
    <input type="text" v-model="email" placeholder="Enter Email" />
    <input type="text" v-model="password" placeholder="Enter password" />
    <button v-on:click="SIGNUP">Sign up</button>
  </div>
  <p>
  <router-link to="/Login">Login</router-link>
  </p>
</template>

<script>
import axios from "axios"
export default {
  // eslint-disable-next-line vue/multi-word-component-names
  name: "Up",
  data() {
    return {
      name: '',
      email: '',
      password: '',
    };
  },
  methods: {
    async SIGNUP() {
      console.warn(this.name, this.email, this.password);
      var result = await axios.post("http://localhost:3000/users",{
      email: this.email,
      name:this.name,
      password:this.password
      });
      console.warn(result);
      if(result.status==201)
      {
         alert("signup done")
        this.$router.push({name:'Login'})
      }
    },
  },

};
</script>
<style>
{
  margin: 0px;
}
.register input {
  width: 300px;
  height: 40px;
  padding-left: 20px;
  display: block;
  margin-bottom: 30px;
  margin-left: auto;
  margin-right: auto;
}
.register button {
  width: 300px;
  height: 40px;
  border: sandybrown;
  color: azure;
  background-color: black;
}
</style>
