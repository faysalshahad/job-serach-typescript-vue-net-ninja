<template>
  <div class="app">
    <header>
      <div class="order">
        <button @click="handleClick('title')">Order by Title</button>
        <button @click="handleClick('salary')">Order by Salary</button>
        <button @click="handleClick('location')">Order by Location</button>
      </div>
    </header>
    <JobList :jobsJList="jobs" :orderJList="order"></JobList>
  </div>
</template>

<script lang="ts">
  import { defineComponent, reactive, ref, toRefs } from 'vue'
  import job from './types/Job'
  import JobList from './components/JobList.vue'
  import OrderTerm from './types/OrderTerm'

  export default defineComponent({
    name: 'App',
    components: { JobList },
    setup() {
      const jobs = ref<job[]>([
        {
          title: 'Software Engineer',
          location: 'New York',
          salary: 120000,
          id: '1',
          description: 'Develop and maintain software applications.'
        },
        {
          title: 'Data Scientist',
          location: 'San Francisco',
          salary: 130000,
          id: '2',
          description: 'Analyze and interpret complex data.'
        },
        {
          title: 'Web Developer',
          location: 'Los Angeles',
          salary: 110000,
          id: '3',
          description: 'Build and maintain websites.'
        },
        {
          title: 'Product Manager',
          location: 'Chicago',
          salary: 140000,
          id: '4',
          description: 'Oversee product development and strategy.'
        },
        {
          title: 'UX Designer',
          location: 'Seattle',
          salary: 115000,
          id: '5',
          description: 'Design user-friendly interfaces.'
        },
        {
          title: 'DevOps Engineer',
          location: 'Austin',
          salary: 125000,
          id: '6',
          description: 'Manage and automate infrastructure.'
        },
        {
          title: 'Full Stack Developer',
          location: 'Boston',
          salary: 135000,
          id: '7',
          description: 'Develop both front-end and back-end components.'
        },
        {
          title: 'Mobile App Developer',
          location: 'Miami',
          salary: 120000,
          id: '8',
          description: 'Create mobile applications for iOS and Android.'
        },
        {
          title: 'Cloud Engineer',
          location: 'Denver',
          salary: 130000,
          id: '9',
          description: 'Design and manage cloud infrastructure.'
        },
        {
          title: 'AI Engineer',
          location: 'Atlanta',
          salary: 145000,
          id: '10',
          description: 'Develop AI models and algorithms.'
        },
        {
          title: 'Blockchain Developer',
          location: 'Phoenix',
          salary: 150000,
          id: '11',
          description: 'Build decentralized applications on blockchain.'
        },
        {
          title: 'Cybersecurity Analyst',
          location: 'Dallas',
          salary: 125000,
          id: '12',
          description: 'Protect systems and networks from cyber threats.'
        },
        {
          title: 'Network Engineer',
          location: 'Orlando',
          salary: 120000,
          id: '13',
          description: 'Design and maintain network systems.'
        },
        {
          title: 'Database Administrator',
          location: 'Philadelphia',
          salary: 115000,
          id: '14',
          description: 'Manage and optimize database systems.'
        },
        {
          title: 'Systems Analyst',
          location: 'Portland',
          salary: 130000,
          id: '15',
          description: 'Analyze and improve IT systems.'
        }
      ])

      const order = ref<OrderTerm>('title')

      const handleClick = (term: OrderTerm) => {
        order.value = term
        // Implement sorting logic here based on term
      }
      return {
        jobs,
        handleClick,
        order
      }
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
  header .title {
    display: flex;
    justify-content: center;
  }
  header img {
    width: 60px;
    margin-right: 20px;
  }
  header h1 {
    font-size: 3em;
  }
</style>
