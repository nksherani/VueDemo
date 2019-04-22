<template>
  <div>
    <h1>Customer Portal</h1>
    <h2>Add Customer</h2>
    <table align="center">
        <tr>
            <th>Customer Name</th>
            <td><input v-model="form.CustomerName" class="input" type="text" placeholder="Name"></td>
        </tr>
        <tr>
            <th>Address</th>
            <td><input v-model="form.Address" class="input" type="text" placeholder="Address"></td>
        </tr>
        <tr>
            <th>ZIP</th>
            <td><input v-model="form.Zip" class="input" type="text" placeholder="ZIP"></td>
        </tr>
        <tr>
            <th>City</th>
            <td><input v-model="form.City" class="input" type="text" placeholder="City"></td>
        </tr>
        <tr>
            <th>Telephone</th>
            <td><input v-model="form.Telephone" class="input" type="text" placeholder="Telephone"></td>
        </tr>
        <tr>
            <th>Contact First</th>
            <td><input v-model="form.ContactFirst" class="input" type="text" placeholder="Contact First"></td>
        </tr>
        <tr>
            <th>Contact Last</th>
            <td><input v-model="form.ContactLast" class="input" type="text" placeholder="Contact Last"></td>
        </tr>
         <tr>
             <th></th>
            <td> <button v-on:click="ClickEventHandler()">Submit</button> </td>
        </tr>
    </table>

  
  </div>
</template>

<script lang="ts">
import { Component, Vue } from 'vue-property-decorator';
import axios from "axios";

@Component
export default class Add extends Vue 
{
    form=null;
    data(){
        return {
            form : {
              CustomerName: '',
              Address: '',
              Zip: '',
              City: '',
              Telephone: '',
              ContactFirst: '',
              ContactLast: ''
            }
        }
    }
    ClickEventHandler(){
        console.log(this.form);
        axios.post('http://localhost:52146/api/Customers/PostCustomer', this.form)

            .then((response) => {
                console.log(response);
                window.location.href='/';
            })
            .catch((error) => {
                console.log(error);
            })
    }
    mounted() { 
      console.log('mounted method');
  }
}
</script>
<style <style lang="scss" scoped>

table {
  font-family: "Trebuchet MS", Arial, Helvetica, sans-serif;
  border-collapse: collapse;
  width: 30%;
}

td,  th {
  border: 1px solid white;
}

tr:nth-child(even){background-color: #f2f2f2;}

 tr:hover {background-color: #ddd;}

 th {
  text-align: left;
  color: black;
}
input{
    width: 100%;
    padding: 0%;
    margin: 0%;
    height: 25px;
}
 .navbar-default{
  background-color: #4CAF50;
  font-size: 18px;
  color: #ddd;
}
.nav-link ,.nav-link:hover{
  font-size: 18px;
  color: white;
  font-weight: bold;
}
form{
  padding: 50px;
}
.form-control{
  max-width: 400px;
}

h1,h2{
  width: 100%;
  background-color: #4CAF50;
  color: #ddd;
  margin:0%
}

</style>