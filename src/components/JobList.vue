<template>
  <div class="job-list">
    <p>ordered by {{ order }}</p>
    <transition-group tag="ul" name="list">
      <li v-for="job in orderedJobs" :key="job.id">
        <h2>{{ job.title }} in {{ job.location }}</h2>
        <div class="salary">
          <p>₹ {{ job.salary }} rupees</p>
        </div>
        <div class="description">
          <p>
            Lorem ipsum dolor sit amet consectetur adipisicing elit. Iusto, qui labore. Quisquam
            facilis, tempora provident veniam qui dolores nihil sapiente eius, esse quis iste
            ducimus soluta incidunt sint exercitationem sequi, quas quam magnam ullam numquam!
            Cupiditate ducimus sit asperiores placeat! Possimus quas cupiditate magnam ut iusto
            ullam nam eius, esse totam ea molestias ab mollitia accusantium quibusdam voluptas
            temporibus quam!
          </p>
        </div>
      </li>
    </transition-group>
  </div>
</template>

<script setup lang="ts">
import { computed } from 'vue'
import type { Job } from '@/types/Job'
import type { OrderTerm } from '@/types/OrderTerm'
import type { PropType } from 'vue'

const props = defineProps({
  jobs: {
    required: true,
    type: Array as PropType<Job[]>
  },
  order: {
    required: true,
    type: String as PropType<OrderTerm>
  }
})

// const orderedJobs = computed(() => {
//   return props.jobs.sort((a:Job,b:Job)=> {
//       return a[props.order] > b[props.order] ? 1 : -1
//     })

// })

const orderedJobs = computed(() => {
  return [...props.jobs].sort((a: Job, b: Job) => {
    return a[props.order] > b[props.order] ? 1 : -1
  })
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
