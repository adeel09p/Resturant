<template>
  <Header0 />
  <router-view />
  <h1>welcome to Update Restaurant page</h1>
  <form class="add">
    <input type="text " placeholder="Enter Name" v-model="restaurant.name" />
    <input
      type="text"
      placeholder="Enter Address"
      v-model="restaurant.address"
    />
    <input
      type="text"
      placeholder="Enter Contact"
      v-model="restaurant.contact"
    />
    <router-link to="/Home">
    <button v-on:click="Update01()">Update Restaurant</button>
    </router-link>
  </form>
</template>
<script>
// eslint-disable-next-line no-unused-vars
import axios from "axios";
import Header0 from "./Header.vue";
export default {
  // eslint-disable-next-line vue/multi-word-component-names
  name: "Update",
  data() {
    return {
      restaurant: {
        name: "",
        address: "",
        contact: "",
      },
    };
  },
  components: {
    Header0,
  },
  async mounted() {
    console.warn(this.$route.params.id);
    let result = await axios.get(
      "http://localhost:3000/restaurant/" + this.$route.params.id
    );
    this.restaurant = result.data;
  },
  methods: {
    async Update01() {
      var result = await axios.put(
        "http://localhost:3000/restaurant/" + this.$route.params.id,
        {
          name: this.restaurant.name,
          address: this.restaurant.address,
          contact: this.restaurant.contact,
        }
      );
      console.warn(result);
    if(result.status==200)
    {
      this.$router.push({path:'/'})
    }
      
      
    },
    
  },
  
};
</script>
