<template>
  <Header0 />
  <h1>welcome to Add Restaurant page</h1>
  <form class="add">
    <input type="text " placeholder="Enter Name" v-model="restaurant.name" />
    <input type="text" placeholder="Enter Address" v-model="restaurant.address" />
    <input type="text" placeholder="Enter Contact" v-model="restaurant.contact"  />
   <router-link to="/Home">
    <button v-on:click="Add01">Add New Restaurant</button>
    </router-link>
  </form>
</template>
<script>
// eslint-disable-next-line no-unused-vars
import axios from"axios";
import Header0 from "./Header.vue";
export default {
  // eslint-disable-next-line vue/multi-word-component-names
  name: "Add",
  data() {
    return {
      restaurant: {
        name: '',
      address: '',
      contact: '',
    },
     
    };
  },
  components: {
    Header0,
  },
  methods: {
   async  Add01() {
      console.warn(this.name, this.address, this.contact);
      var result = await axios.post("http://localhost:3000/restaurant",{
      name:   this.restaurant.name,
      address:this.restaurant.address,
      contact:this.restaurant.contact
      });
      console.warn(result);
      if(result.status==201)
      {
     this.$router.push({path:'/'})
      }
  
}
  }
}
</script>