<script setup lang="ts">
import { ref } from 'vue';
import type { Ref } from 'vue';
import type Job from '@/types/Job';
import type OrderTerm from '@/types/OrderTerm';
import JobList from './components/JobList.vue';

// const name: Ref<string | number> = ref('Mario')
// const age = ref<string | number>(20)

// const changeName = (newName: string) => {
//   name.value = newName
// }

// const changeAge = (newAge: string | number) => {
//   age.value = newAge
// }

// const person = ref({
//   firstName: "Micki",
//   age: 20 as string | number,
// })

const jobs = ref<Job[]>([
  { title: 'farm worker', location: 'lon lon ranch', salary: 30000, id: '1' },
  { title: 'quarryman', location: 'death mountain', salary: 40000, id: '2' },
  { title: 'flute player', location: 'the lost woods', salary: 35000, id: '3' },
  { title: 'fisherman', location: 'lake hylia', salary: 21000, id: '4' },
  { title: 'prison guard', location: 'gerudo valley', salary: 32000, id: '5' }
])

const order = ref<OrderTerm>('title')

const handleClick = (term: OrderTerm) => {
  order.value = term
}


</script>

<template>
  <div class="app">
    <header>
      <div class="order">
        <button @click="handleClick('title')">Order by Title</button>
        <button @click="handleClick('salary')">Order by Salary</button>
        <button @click="handleClick('location')">Order by Location</button>
        <!-- <div v-for="job in jobs" :key="job.id">
          {{ job.title }}
        </div> -->
        <!-- <h2 @click="changeName('Yoshi')">{{ name }}</h2>
          <h3 @click="changeAge(25)">{{ age }}</h3>
          <h2>{{ person.firstName }}</h2>
          <h3>{{ person.age }}</h3> -->
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
</style>
