<template>
  <div class="app">
    <header>
      <button @click="handleClick('title')">Order by Title</button>
      <button @click="handleClick('salary')">Order by Salary</button>
      <button @click="handleClick('location')">Order by Location</button>
    </header>
    <JobList :jobs="jobs" :order="order" />
  </div>
</template>

<script lang="ts">
import { defineComponent, ref } from "vue";
import Job from "./types/job";
import OrderTerm from "./types/OrderTerm";
import JobList from "./components/JobList.vue";

export default defineComponent({
  name: "App",
  components: {
    JobList,
  },
  setup() {
    const jobs = ref<Job[]>([
      {
        title: "farm worker",
        location: "lon lon ranch",
        salary: 30000,
        id: "1",
      },
      {
        title: "quarryman",
        location: "death mountain",
        salary: 40000,
        id: "2",
      },
      {
        title: "flute player",
        location: "the lost woods",
        salary: 35000,
        id: "3",
      },
      { title: "fisherman", location: "lake hylia", salary: 21000, id: "4" },
      {
        title: "prison guard",
        location: "gerudo valley",
        salary: 32000,
        id: "5",
      },
    ]);

    const order = ref<OrderTerm>("title");

    const handleClick = (term: OrderTerm) => {
      order.value = term;
    };

    return { jobs, handleClick, order };
  },
});
</script>

<style>
header {
  display: flex;
  /* display: inline-block; */
  text-align: center;
  margin: 5px 10px;
  justify-content: center;
  gap: 15px;
}

header button {
  height: 30px;
  width: 150px;
  text-align: center;
  border-radius: 5px;
  border: 1px solid grey;
}
</style>
