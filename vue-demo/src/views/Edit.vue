<template>
  <div>
    <h1>Customer Portal</h1>
    <h2>Edit Customer</h2>
    <table v-if="Customer" align="center">
        <tr>
            <th>Customer Name</th>
            <td><input v-model="Customer.CustomerName" class="input" type="text" placeholder="Name"></td>
        </tr>
        <tr>
            <th>Address</th>
            <td><input v-model="Customer.Address" class="input" type="text" placeholder="Address"></td>
        </tr>
        <tr>
            <th>ZIP</th>
            <td><input v-model="Customer.Zip" class="input" type="text" placeholder="ZIP"></td>
        </tr>
        <tr>
            <th>City</th>
            <td><input v-model="Customer.City" class="input" type="text" placeholder="City"></td>
        </tr>
        <tr>
            <th>Telephone</th>
            <td><input v-model="Customer.Telephone" class="input" type="text" placeholder="Telephone"></td>
        </tr>
        <tr>
            <th>Contact First</th>
            <td><input v-model="Customer.ContactFirst" class="input" type="text" placeholder="Contact First"></td>
        </tr>
        <tr>
            <th>Contact Last</th>
            <td><input v-model="Customer.ContactLast" class="input" type="text" placeholder="Contact Last"></td>
        </tr>
         <tr>
             <th></th>
            <td> <button v-on:click="ClickEventHandler()">Update</button> </td>
        </tr>
    </table>

  </div>
</template>

<script lang="ts">
import { Component,Prop, Vue } from 'vue-property-decorator';
import axios from "axios";

@Component
export default class Edit extends Vue 
{
    // @Prop(String)
     Customer={};
    data(){
        return {
            Customer: null
        }
    }
    render(){
        
        console.log('data method');
    }
    ClickEventHandler(){
        console.log(this.Customer);
        axios.post('http://localhost:52146/api/Customers/PostCustomer', this.Customer)

            .then((response) => {
                console.log(response);
                window.location.href='/';
            })
            .catch((error) => {
                console.log(error);
            })
    }
  mounted() { 
      var id = this.$route.params.custid;
            console.log(this.$route.params.custid+'mounted method');

      axios({ method: "GET", "url": "http://localhost:52146/api/Customers/"+id }).then(result => {
                console.log(result.data);
                this.Customer = result.data;
            }, error => {
                console.error(error);
            });
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