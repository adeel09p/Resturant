<template>
  <router-view/>
</template>

<script>
//import Up from "./components/SignUp.vue";


export default {
  name: "App",
  // components: {
  //   Up,
  // },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
body
{
  margin: 0;
  padding: 0;

}
.register input,.add input {
  width: 300px;
  height: 40px;
  padding-left: 20px;
  display: block;
  margin-bottom: 30px;
  margin-left: auto;
  margin-right: auto;
}
 button {
  width: 300px;
  height: 40px;
  border: sandybrown;
  color:rgba(52, 170, 168, 0.158);
  background-color: black;
  cursor: pointer;
}
</style>
