<template>
  <div>
    <h1>Customer Portal</h1>
    <h2>Edit Customer</h2>
    <table v-if="Customer">
        <tr>
            <th>Customer Name</th>
            <td><input v-model="Customer.CustomerName" class="input" type="text" placeholder="Text input"></td>
        </tr>
        <tr>
            <th>Address</th>
            <td><input v-model="Customer.Address" class="input" type="text" placeholder="Text input"></td>
        </tr>
        <tr>
            <th>ZIP</th>
            <td><input v-model="Customer.Zip" class="input" type="text" placeholder="Text input"></td>
        </tr>
        <tr>
            <th>City</th>
            <td><input v-model="Customer.City" class="input" type="text" placeholder="Text input"></td>
        </tr>
        <tr>
            <th>Telephone</th>
            <td><input v-model="Customer.Telephone" class="input" type="text" placeholder="Text input"></td>
        </tr>
        <tr>
            <th>Contact First</th>
            <td><input v-model="Customer.ContactFirst" class="input" type="text" placeholder="Text input"></td>
        </tr>
        <tr>
            <th>Contact Last</th>
            <td><input v-model="Customer.ContactLast" class="input" type="text" placeholder="Text input"></td>
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
