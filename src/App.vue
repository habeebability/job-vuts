<script setup lang="ts">
import { ref } from 'vue'
// @ts-ignore
import JobList from './components/JobList.vue'
// @ts-ignore
import Job from './types/Job'
import OrderTerm from './types/OrderTerm'

const jobs = ref<Job[]>([
  {
    id: '1',
    title: 'Frontend Developer',
    location: 'Remote',
    salary: 58000
  },
  { title: 'quarryman', location: 'death mountain', salary: 40000, id: '2' },
  { title: 'flute player', location: 'the lost woods', salary: 35000, id: '3' },
  { title: 'fisherman', location: 'lake hylia', salary: 21000, id: '4' },
  { title: 'prison guard', location: 'gerudo valley', salary: 32000, id: '5' }
])

const order = ref<OrderTerm>('title')

const handleFilter = (term: OrderTerm) => {
  order.value = term
}
</script>

<template>
  <div class="app">
    <header>
      <div class="title">
        <svg
          xmlns="http://www.w3.org/2000/svg"
          fill="none"
          viewBox="0 0 24 24"
          stroke-width="1.5"
          stroke="currentColor"
          class="w-6 h-6"
        >
          <path
            stroke-linecap="round"
            stroke-linejoin="round"
            d="M21 8.25c0-2.485-2.099-4.5-4.688-4.5-1.935 0-3.597 1.126-4.312 2.733-.715-1.607-2.377-2.733-4.313-2.733C5.1 3.75 3 5.765 3 8.25c0 7.22 9 12 9 12s9-4.78 9-12z"
          />
        </svg>
        <h1>Job Vuts</h1>
      </div>
      <div class="order">
        <button @click="handleFilter('title')">order by title</button>
        <button @click="handleFilter('salary')">order by salary</button>
        <button @click="handleFilter('location')">order by location</button>
      </div>
    </header>
    <JobList :jobs="jobs" :order="order" />
  </div>
</template>

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
button:hover {
  background-color: #1195c9;
  color: white;
  transform: translate(0em, -0.2em);
}
button:active {
  transform: translate(0em, 0.2em);
}
header .title {
  display: flex;
  justify-content: center;
}
header svg {
  width: 60px;
  margin-right: 20px;
}
header h1 {
  font-size: 3em;
}
</style>
