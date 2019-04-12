<template>
  <div v-if="customers">
    <ul id="example-1">
    <li  v-for="(item, i) in customers" :key="item.id">
    {{ item.CustomerName }}
  </li>
</ul>
  </div>
</template>

<script>
import axios from "axios";
let customers = [];
export default {
  name: 'Index',
  data: function () {
            return {
                customers: []
            };
        },
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

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
