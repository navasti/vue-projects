<template>
  <div class="app">
    <header>
      <div class="title">
        <h1>Hyrule Jobs</h1>
      </div>
      <div class="order">
        <button @click="handleOrderClick('title')">Order by title</button>
        <button @click="handleOrderClick('salary')">Order by salary</button>
        <button @click="handleOrderClick('location')">Order by location</button>
      </div>
    </header>
    <JobList :jobs="jobs" :order="order" />
  </div>
</template>

<script lang="ts">
import { defineComponent, ref } from "vue";
// Components
import JobList from "./components/JobList.vue";
// Types
import Job from "./types/Job";
import OrderTerm from "./types/OrderTerm";
// Data
import jobsData from "./jobs";

export default defineComponent({
  name: "App",
  components: { JobList },
  setup() {
    const jobs = ref<Job[]>(jobsData);
    const order = ref<OrderTerm>("title");

    const handleOrderClick = (term: OrderTerm) => {
      order.value = term;
    };

    return { jobs, handleOrderClick, order };
  },
});
</script>

<style scoped>
header {
  text-align: center;
}
header .order {
  margin-top: 20px;
}
button {
  margin: 0 10px;
  color: #17bf66;
  border: 3px solid #17bf66;
  background: #fff;
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
