<template>
  <div>
    <h1>Customer Portal</h1>
    <h2>Add Customer</h2>
    <table>
        <tr>
            <th>Customer Name</th>
            <td><input v-model="form.CustomerName" class="input" type="text" placeholder="Text input"></td>
        </tr>
        <tr>
            <th>Address</th>
            <td><input v-model="form.Address" class="input" type="text" placeholder="Text input"></td>
        </tr>
        <tr>
            <th>ZIP</th>
            <td><input v-model="form.Zip" class="input" type="text" placeholder="Text input"></td>
        </tr>
        <tr>
            <th>City</th>
            <td><input v-model="form.City" class="input" type="text" placeholder="Text input"></td>
        </tr>
        <tr>
            <th>Telephone</th>
            <td><input v-model="form.Telephone" class="input" type="text" placeholder="Text input"></td>
        </tr>
        <tr>
            <th>Contact First</th>
            <td><input v-model="form.ContactFirst" class="input" type="text" placeholder="Text input"></td>
        </tr>
        <tr>
            <th>Contact Last</th>
            <td><input v-model="form.ContactLast" class="input" type="text" placeholder="Text input"></td>
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
