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
        <tr>
          <td><a href="detail.html">001</a></td>
          <td>Tanaka</td>
        </tr>
        <tr>
          <td><a href="detail.html">002</a></td>
          <td>Tamura</td>
        </tr>
        <tr>
          <td><a href="detail.html">003</a></td>
          <td>Nakata</td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<script lang="ts">
import { Component, Vue } from 'vue-property-decorator';
import SearchBox from '@/components/SearchBox.vue'; // @ is an alias to /src

@Component({
  components: {
      SearchBox
  },
})
export default class Home extends Vue {
  public searchButtonClicked(text: string) {
    console.log("Receive click event in Home.vue: " + text)
  }
}
</script>
