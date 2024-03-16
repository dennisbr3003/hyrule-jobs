<template>
  <div class="app">
    <div>
      {{ jobs }}
    </div>
  </div>
</template>

<script lang="ts">
import { defineComponent, ref } from 'vue'
import { Job } from './types/types'

export default defineComponent({
  name: 'App',
  components: {},
  setup() {
    const jobs = ref<Job[]>([
      {title: 'Test Engineer', location: 'Bangalore, India', salary: 1000, id: '1'},
      {title: 'Social Hacker', location: 'New Delhi, India', salary: 23000, id: '2'},
      {title: 'UX Designer', location: 'University of Bombay, India', salary: 1000, id: '3'},
      {title: 'JS/ABL developer', location: 'Helmond, Netherlands', salary: 19000, id: '4'},
      {title: 'Test Engineer (Junior)', location: 'Bangalore, India', salary: 750, id: '5'},
    ])
    return { jobs }
  }
})
</script>

<style scoped>

</style>