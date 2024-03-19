<template>
    <div class="joblist">
        <p>Ordered by {{ order }}</p>
        <TransitionGroup name="jobs" tag="ul"> <!-- replace UL tag with transition-group add a class -->
            <li v-for="job in orderedJobs" :key="job.id">
                <h2>{{ job.title }} in {{ job.location }}</h2>
                <div class="salary">
                    <img src="@/assets/rupee.svg" alt="ri">
                    <p>{{ job.salary }} rupees</p>
                </div>
                <div class="description">Lorem ipsum dolor sit amet, consectetur adipisicing elit. Ut doloremque, esse incidunt illum tenetur, blanditiis laboriosam labore voluptates quis laborum, molestias dignissimos aperiam nihil nesciunt expedita repellat nostrum! Deleniti, aliquid.</div>
            </li>
        </TransitionGroup>
    </div>
</template>

<script lang="ts">

import { defineComponent, PropType, computed } from 'vue'
import type { Job, OrderTerm } from '@/types/types'

export default defineComponent({
    props: {
        jobs: {
            required: true,
            type: Array as PropType<Job[]>
        },
        order: {
            required: true,
            type: String as PropType<OrderTerm>
        }
    },
    setup (props) {
        const orderedJobs = computed(() => {
            return [...props.jobs].sort((a:Job, b:Job) => { // this is done to NOT destruct the array but to create a temp array and sort that using the spread operator. Otherwise error!
               return a[props.order] > b[props.order] ? 1 : -1 // sort return 1, 0 or -1. We get pairs of elements (a and b) of type job. props.order is the field name on which to sort
                                                         // 1 : elements DO NOT switch places, -1 elements DO switch places
            }) 
        })
        return { orderedJobs }        
    }
})
</script>

<style scoped>
.joblist {
    max-width: 960px;
    margin: 40px auto;
}
.joblist ul {
    padding: 0;
}
.joblist li {
    list-style-type: none;
    background: white;
    padding: 16px;
    margin: 16px 0;
    border-radius: 4px;
}
.joblist h2 {
    margin: 0 0 10px;
    text-transform: capitalize;
}
.salary {
    display: flex;    
}
.salary img {
    width: 30px;
}
.salary p {
    color: #17bf66;
    font-weight: bold;
    margin: 10px 4px;
}
.jobs-move{
    transition: all 1s;
}
</style>