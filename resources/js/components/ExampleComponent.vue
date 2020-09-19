<template>
<div>
  <input type="text" id="input" v-model="message">
  <p>{{message}}</p>
  <ul>
      <li v-for="name in names" v-text="name"></li>
  </ul>
  <input type="name" v-model="newName">
  <button @click="addName">Add name</button>
</div>
</template>

<script>
import axios from "axios";
    export default {
        
            data: function() {
                return {
                    message: 'Hello',
                    names: ['John', 'Doe', 'Mar', 'Dan', 'Apr'],
                    newName: ''
                }
            },
            methods: { 
                addName() {
                    this.names.push(this.newName),
                    this.newName = ''
                }
                 },
        mounted() {
            axios.get('https://httpbin.org/get').then(response => 
            this.names.push(response.data.origin)),
            console.log('Component mounted.')
        }
        
    }
</script>
