<template>
    <div class="job-list">
        <h3>Ordered by {{ order }}</h3>
        <ul>
            <li v-for="job in orderedData" :key="job.id">
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
import { computed, defineComponent, PropType } from 'vue';
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
    },
    setup(props) {
        const orderedData = computed(() => {
            return [...props.jobs].sort((a: Job, b: Job) => {
                return a[props.order] > b[props.order] ? 1 : -1
            });
        })

        return { orderedData }
    }

})
</script>

<style scoped>
ul {
    list-style-type: none;
}

.job-list {
    margin-left: 40px auto;
}

.job-list ul {
    padding: 0;
}

.job-list li {
    list-style-type: none;
    background: white;
    border-radius: 10px;
    padding: 10px 15px;
    margin: 10px;
}

.job-list h3 {
    text-align: center;
}

.description {
    padding-bottom: 10px
}

.salary {
    color: #33ff99;
    font-weight: bold;
}
</style>