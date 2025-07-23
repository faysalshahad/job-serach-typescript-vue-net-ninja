<template>
  <div class="job-list">
    <p>Sorted by: {{ orderJList }}</p>
    <ul>
      <li v-for="job in sortedJobs" :key="job.id">
        <h3>{{ job.title }} in {{ job.location }}</h3>
        <div class="salary">
          <p>{{ job.salary }} dollars</p>
        </div>
        <div class="description">
          <p>{{ job.description }}</p>
        </div>
      </li>
    </ul>
  </div>
</template>

<script lang="ts">
  import { computed, defineComponent, PropType } from 'vue'
  import Job from '../types/Job'
  import OrderTerm from '../types/OrderTerm'

  export default defineComponent({
    props: {
      jobsJList: {
        type: Array as PropType<Job[]>,
        required: true
      },
      orderJList: {
        type: String as PropType<OrderTerm>,
        // default: 'title',
        required: true
      }
    },
    setup(props) {
      const sortedJobs = computed(() => {
        return [...props.jobsJList].sort((a: Job, b: Job) => {
          if (a[props.orderJList] < b[props.orderJList]) return -1
          if (a[props.orderJList] > b[props.orderJList]) return 1
          return 0
          // or we can use a ternary operator:
          //return a[props.orderJList] > b[props.orderJList] ? 1 : -1
        })
      })
      return {
        sortedJobs
      }
    }
  })
</script>

<style scoped>
  .job-list {
    max-width: 960px;
    margin: 40px auto;
  }
  .job-list ul {
    padding: 0;
  }
  .job-list li {
    list-style-type: none;
    background: white;
    padding: 16px;
    margin: 16px 0;
    border-radius: 4px;
  }
  .job-list h2 {
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
  .list-move {
    transition: all 1s;
  }
</style>
