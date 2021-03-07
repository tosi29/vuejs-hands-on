<template>
  <div class="detail">
    <h1>This is detail page</h1>
    <span>User ID: {{ userid }}</span>
  </div>
</template>

<script lang="ts">
import { Component, Vue } from 'vue-property-decorator';

@Component
export default class Detail extends Vue {
    userid = '';

    created() {
        this.userid = this.$route.params.id
        console.log(this.userid)
    }
}
</script>
