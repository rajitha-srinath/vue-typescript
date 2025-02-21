<template>
    <div class="job-list">
        <p>Ordered by {{ order }}</p>
        <ul>
            <li v-for="job in jobs" :key="job.id">
                <h2>{{ job.title }} in {{ job.location }}</h2>
                <div class="salary">
                    <p>{{ job.salary }}</p>
                </div>
                <div class="description">
                    Lorem ipsum dolor sit, amet consectetur adipisicing elit. Dolorum necessitatibus quas rerum
                    cupiditate incidunt, ducimus placeat quod voluptate? Enim dolores nulla tenetur hic at eum
                    recusandae officia accusamus. Quas expedita rem dolores explicabo ex, fugiat quasi cupiditate.
                    Distinctio, minima repellendus.
                </div>
            </li>
        </ul>
    </div>
</template>

<script lang="ts">
import { defineComponent, PropType } from 'vue';
import Job from '@/types/job';
import OrderTerm from '@/types/OrderTerm';

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
    }
})
</script>

<style scoped>
ul {
    list-style-type: none;
}
.job-list li {
    margin: 20px 20px;
    background-color: #fff;
    padding: 5px 10px;
    border-radius: 10px;
}

.description {
    padding-bottom: 10px
}

.salary {
    color: #33ff99;
    font-weight: bold;
}
</style>