<script setup lang="ts">
import { computed, type PropType } from 'vue';
import type Job from '@/types/Job';
import type OrderTerm from '@/types/OrderTerm';

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

const orderedJobs = computed(() => {
    return [...props.jobs].sort((a: Job, b: Job) => {
        return a[props.order] > b[props.order] ? 1 : -1
    })
})

</script>

<template>
    <div class="job-list">
        <p>Ordered by {{ order }}</p>
        <TransitionGroup name="list" tag="ul">
            <li v-for="job in orderedJobs" :key="job.id">
                <h2>{{ job.title }} in {{ job.location }}</h2>
                <div class="salary">
                    <p>{{ job.salary }} rupees</p>
                </div>
                <div class="description">
                    <p>
                        Lorem ipsum dolor sit amet, consectetur adipisicing elit. A dolore officiis perspiciatis minima, sit
                        accusantium distinctio maiores. Reprehenderit praesentium amet harum deserunt id sint ut minus
                        maiores atque
                        tempore? Dolor.
                    </p>
                </div>
            </li>
        </TransitionGroup>
    </div>
</template>


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