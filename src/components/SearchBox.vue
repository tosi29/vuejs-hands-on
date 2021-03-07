<template>
  <div>
    <input type="text" v-model="text" placeholder="Type username to find"> 
    <button @click="onClick">Search</button>
  </div>
</template>

<script lang="ts">
import { Component, Emit, Vue } from 'vue-property-decorator';

@Component
export default class SearchBox extends Vue {
  text = '';

  @Emit() // Emit click event
  public click(text: string) {
    console.log("Click event emitted: " + text)
  }

  // Click event handler of this component
  public onClick() {
    console.log("onClick() from search button");
    this.click(this.text); // Emit click event
  }
}
</script>

<style scoped lang="scss">
</style>
