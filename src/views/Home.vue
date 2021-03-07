<template>
  <div class="home" id="app">
    <!-- 
    <img alt="Vue logo" src="../assets/logo.png">
    <HelloWorld msg="Welcome to Your Vue.js + TypeScript App"/>
    -->
    <h3>検索条件</h3>
    <div>
      <search-box @click="searchButtonClicked"></search-box>
    </div>
    <h3>検索結果</h3>
    <table border="1">
      <thead>
        <tr>
          <td>User Id</td>
          <td>User Namme</td>
        </tr>
      </thead>
      <tbody>
        <tr v-for="user in userdata" :key="user.id">
          <td><a href="detail.html">{{ user.id }}</a></td>
          <td>{{ user.name }}</td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<script lang="ts">
import { Component, Vue } from 'vue-property-decorator';
import SearchBox from '@/components/SearchBox.vue'; // @ is an alias to /src
import axios from 'axios';

@Component({
  components: {
      SearchBox
  },
})
export default class Home extends Vue {
  userdata = [
    { "id": "001", "name": "Tanaka" },
    { "id": "002", "name": "Tamura" },
    { "id": "003", "name": "Nakata" }
  ];

  public searchButtonClicked(text: string) {
    console.log("Receive click event in Home.vue: " + text);

    axios.get('http://localhost:3000/users', {
      params: {
        id: text
      }
    })
      .then( (response) => {
        // handle success
        console.log(response);
        this.userdata = response.data;
      })
      .catch( (error) => {
        // handle error
        console.log(error);
      })
      .then( () => {
        // always executed
      });
      
  }
}
</script>
