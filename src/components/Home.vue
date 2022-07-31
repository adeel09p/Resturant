<!-- eslint-disable no-unused-vars -->

<template>
  <Header0 />
  <h1>Hello {{ name }} welcome to home page</h1>
  <table border="3">
    <tr>
      <td colspan="3">Id</td>
      <td colspan="3">Name</td>
      <td colspan="3">Address</td>
      <td colspan="3">Contact</td>
      <td colspan="3">Action</td>
    </tr>
    <tr v-for="item in restaurant" :key="item.id">
      <td colspan="3">{{ item.id }}</td>
      <td colspan="3">{{ item.name }}</td>
      <td colspan="3">{{ item.address }}</td>
      <td colspan="3">{{ item.contact }}</td>
      <td><router-link :to="'/Update/' + item.id">Update</router-link></td>
        <button v-on:click="deleteR(item.id)">Delete</button>
      
    </tr>
  </table>
</template>
<script>
// eslint-disable-next-line no-unused-vars
import Header0 from "./Header.vue";
// eslint-disable-next-line no-unused-vars
import axios from "axios";
export default {
  // eslint-disable-next-line vue/multi-word-component-names
  name: "Home",
  data() {
    return {
      name: "",
      restaurant: [],
    };
  },
  components: {
    Header0,
  },

  mounted() {
    this.loadData();
        let user = localStorage.getItem("user-info");
     if (!user)
      {
      this.$router.push({ name: "Login" });
    }
    
  },
  methods:
{
  async deleteR(id)
  {
    let result=await axios.delete("http://localhost:3000/restaurant/"+id);
    if(result.status==200)
    {
    let result = await axios.get("http://localhost:3000/restaurant");
    this.restaurant = result.data;
    }

  },
  async loadData()
  {
    let user = localStorage.getItem("user-info");
    this.name = JSON.parse(user).name;
    if (!user) {
      this.$router.push({ name: "Up" });
    }
    let result = await axios.get("http://localhost:3000/restaurant");
    this.restaurant = result.data;
  }
}
};
</script>
