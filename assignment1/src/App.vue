<template>
  <div id="app">
    <div class="title">
      <p class="form-title">Customer Details</p>
    </div>
    <div class="inputs">
      <form class="form" v-on:submit.prevent>
        <div class="firstName">
          <label for="fname">First Name</label>
          <input v-model="finame" id="fname" type="text" placeholder="Enter your First Name" required>
        </div>
        <div class="lastNmae">
          <label for="lname">Last Name</label>
          <input v-model="laname" id="lname" type="text" placeholder="Enter your Last Name" required>
        </div>
        <div class="address">
          <label for="p-address">Address</label>
          <input v-model="address" id="p-address" type="text" placeholder="Enter your Address" required>
        </div>
        <div class="email">
          <label for="email">Email</label>
          <input v-model="email" id="email" type="email" placeholder="Enter your Email" required>
        </div>
      </form>
      <div class="button">
          <button type="submit" @click="addData">Add</button>
        </div>
    </div>
    <div class="tables">
      <table>
        <tr v-for="(item, index) in tabelData" :key="index">
        <td class="td1" :class="{red: item.isActive}">{{ item.fname }}</td>
        <td class="td2" :class="{red: item.isActive}">{{ item.sname }}</td>
        <td class="td3" :class="{red: item.isActive}">{{ item.address }}</td>
        <td class="td4" :class="{red: item.isActive}">{{ item.eMail }}</td>
        <td class="td5">
          <div class="del-c">
          <span class="del" @click="deleteRow(index)">X</span>
          <span class="tek" @click="colorChange(index)">&#10003;</span>
          </div>
        </td>
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
      finame: "",
      laname: "",
      address: "",
      email: "",
      isRed: false,
      tabelData: [],
    }

  },
  methods: {

    deleteRow(index){
      this.tabelData.splice(index);
    },

    colorChange(index){
      let isAc = this.tabelData[index].isActive;
      this.tabelData[index].isActive = !isAc;
      console.log("color change function working");
      this.isRed = !this.isRed;
    },

    // tabelCchange(index){
    //   this.tabelData.colorChange(index);
    // },

    emailValidate() {
      let result = true
        for(let element of this.tabelData) {
          console.log("Email Matches");

          if(element.eMail === this.email) {
            result = false
          } else{
            console.log("Email Doesn't Exist")
            result  = true
          }
        }
        return result
    },

    addData(){
      console.log('72 called', this.emailValidate())
      if(this.finame && this.laname && this.address && this.email && this.emailValidate()) {
      this.tabelData.push({fname: this.finame, sname: this.laname, address: this.address, eMail: this.email, isActive: false})
      }
      this.finame = "";
      this.laname = "";
      this.email = "";
      this.address = "";
    },
  }
}
</script>

<style>
*{
  margin: 0;
  padding: 0;
}
body{
  background-color: rgba(199, 236, 238,1.0);
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  width: 60%;
  min-height: 100vh;
  margin-left: auto;
  margin-right: auto;
  margin-top: 60px;
}

.red{
  color: red;
}

.title{
  border-bottom: 5px solid rgba(223, 249, 251,1.0);
  margin-bottom: 10px;
}

.form-title{
  font-size: 3rem;
  color: rgba(83, 92, 104,1.0);
}

.inputs{
  display: flex;
  flex-direction: row;
  min-height: 40px;
  margin: 10px auto;
}

form{
  display: grid;
  grid-template-columns: 1fr 1fr 1fr 1fr;
}

label{
  height: 30px;
  margin-bottom: 10px;
  font-size: 22px;
  color: rgba(83, 92, 104,1.0);
}


.firstName{
  grid-column-start: 1;
  grid-column-end: 2;
}

.lastName{
  grid-column-start: 2;
  grid-column-end: 3;
}

.address{
  grid-column-start: 3;
  grid-column-end: 4;
}

.email{
  grid-column-start: 4;
  grid-column-end: 5;
}

.button{
  box-sizing: border-box;
  padding: 10px 0 10px 10px;
}

button{
  cursor: pointer;
  grid-column-start: 5;
  grid-column-end: 6;
  width: 50px;
  height: 30px;
  color: rgba(83, 92, 104,1.0);
  border-radius: 5px;
}

.tables{
  width: 100%;
  height: auto;
}

tr, td{
  border: 1px solid rgba(45, 52, 54, 0.6);
  border-collapse: collapse;
}

table{
  display: grid;
  grid-template-columns: 1fr;
}

tr{
  grid-column: 1fr;
  display: grid;
  grid-template-columns: 1fr 1fr 1fr 1fr 100px;
  width: 100%;
  height: auto;
}

.td1{
    grid-column-start: 1;
    grid-column-end: 2; 
}

.td2{
    grid-column-start: 2;
    grid-column-end: 3;
}

.td3{
    grid-column-start: 3;
    grid-column-end: 4; 
}

.td4{
    grid-column-start: 4;
    grid-column-end: 5; 
}

.del-c{
    display: flex;
    align-items: center;
    justify-content: space-evenly;
    grid-column-start: 5;
    grid-column-end: 6; 
}

.del, .tek{
  cursor: pointer;
  box-sizing: border-box;
  padding: 0 5px;
  margin-left: 2px;
  margin-right: 2px;
}

</style>
