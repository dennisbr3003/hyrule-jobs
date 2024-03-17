<template>
  <div class="app">
    <header>
      <div class="order">
        <button @click="handleClick(`title`)">Order by title</button>
        <button @click="handleClick(`salary`)">Order by salary</button>
        <button @click="handleClick(`location`)">Order by location</button>
      </div>
    </header>
    <JobsList :jobs="jobs" :order="order"/>
  </div>
</template>

<script lang="ts">
import { defineComponent, ref } from 'vue'
import JobsList from './components/JobsList.vue'
import { Job, OrderTerm } from './types/types'

export default defineComponent({
  name: 'App',
  components: {JobsList},
  setup() {
    const jobs = ref<Job[]>([
      {title: 'Test Engineer', location: 'Bangalore, India', salary: 1000, id: '1'},
      {title: 'Social Hacker', location: 'New Delhi, India', salary: 23000, id: '2'},
      {title: 'UX Designer', location: 'University of Bombay, India', salary: 1000, id: '3'},
      {title: 'JS/ABL developer', location: 'Helmond, Netherlands', salary: 19000, id: '4'},
      {title: 'Test Engineer (Junior)', location: 'Bangalore, India', salary: 750, id: '5'},
    ])

    const order = ref<OrderTerm>('title')
    const handleClick = (term: OrderTerm) => {
      order.value = term
    }

    return { jobs, handleClick, order }
  }
})
</script>

<style>
  header {
    text-align: center;
  }
  header .order {
    margin-top: 20px;
  }
  button {
    margin: 0 10px;
    color: #1195c9;
    border: 3px solid #1195c9;
    background: #d5f0ff; 
    padding: 8px 16px; 
    border-radius: 4px; 
    cursor: pointer; 
    font-weight: bold;
  }
</style>