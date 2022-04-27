<template>
  <div id="app">
    <p>Customer Details</p>
    <div class="inputs">
      <form v-on:submit.prevent>
        <label for="fname">First Name</label>
        <input v-model="finame" id="fname" type="text" placeholder="Enter your First Name">
        <label for="lname">Last Name</label>
        <input v-model="liname" id="lname" type="text" placeholder="Enter your Last Name">
        <label for="p-address">Address</label>
        <input v-model="address" id="p-address" type="text" placeholder="Enter your Address">
      </form>
      <button>Add</button>
    </div>
    <div class="tables">
      <table>
        <tr>
        <td>{{ finame }}</td>
        <td>{{ liname }}</td>
        <td>{{ address }}</td>
      </tr>
      </table>
    </div>
  </div>
</template>

<script>

export default {
  name: 'App',
  data() {
    return{
      finame: "Sky",
      liname: "High",
      address: "Clouds",
    }

  },
  methods: {

  }
}
</script>

<style>

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  margin-top: 60px;
}

.inputs{
  width: 100%;
}
</style>
