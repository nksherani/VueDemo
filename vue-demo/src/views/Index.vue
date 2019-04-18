<template>
  <div v-if="customers">
    <h1>Customer Portal</h1>
    <router-link to="/add">Add New</router-link>
 <table>
  <tr>
    <th>
      Customer Name
    </th>
    <th>
      Address
    </th>
    <th>
      ZIP
    </th>
    <th>
      City
    </th>
    <th>
      Telephone
    </th>
    <th>
      Contact First
    </th>
    <th>
      Contact Last
    </th>
    <th>
      Created Date
    </th>
    <th>
      Action
    </th>
  </tr>
  <tr v-for="(item, i) in customers" :key="item.id">
    <td>
      {{item.CustomerName}}
    </td>
    <td>
      {{item.Address}}
    </td>
    <td>
      {{item.ZIP}}
    </td>
    <td>
      {{item.City}}
    </td>
    <td>
      {{item.Telephone}}
    </td>
    <td>
      {{item.ContactFirst}}
    </td>
    <td>
      {{item.ContactLast}}
    </td>
    <td>
      {{item.CreatedDate}}
    </td>
    <td>
            <router-link :to="{ name: 'edit', params: {custid: item.CustomerId } }">Edit</router-link>
            <!-- name as specified in routes custid is also specified in routes -->
    </td>
  </tr>
</table>
  </div>
</template>

<script lang="ts">
import { Component, Vue } from 'vue-property-decorator';
import axios from "axios";

@Component
export default class Index extends Vue 
{
    customers = [];
    data(){
        return {
            customers: null
        }
    }
    render(){
        console.log('data method');
    }
    mounted() { 
      axios({ method: "GET", "url": "http://localhost:52146/api/Customers" }).then(result => {
                console.log(result.data);
                this.customers = result.data;
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
  width: 100%;
}

td,  th {
  border: 1px solid #ddd;
  padding: 8px;
}

tr:nth-child(even){background-color: #f2f2f2;}

 tr:hover {background-color: #ddd;}

 th {
  padding-top: 12px;
  padding-bottom: 12px;
  text-align: left;
  background-color: #4CAF50;
  color: white;
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



</style>