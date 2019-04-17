<template>
  <div class="home">
    <Index/>
  </div>
</template>

<script lang="ts">
import { Component, Vue } from 'vue-property-decorator';
import Index from '@/views/Index.vue'; // @ is an alias to /src

@Component({
  components: {
    Index,
  },
})
export default class Home extends Vue {}
</script>
