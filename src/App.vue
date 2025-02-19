<template>
  <div class="app">
    hello, {{ jobs[0].location }}
  </div>
</template>

<script lang="ts">
import { defineComponent, ref } from 'vue';
import Job from './types/job';

export default defineComponent({
  name: 'App',
  components: {},
  setup() {
    const jobs = ref<Job[]>([
      {title: "raaji", id: '1', location: 'colombo', salary: 3000}
    ]);

    return {jobs}
  }
});
</script>

<style>

</style>
