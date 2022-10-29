<template>
  <div>
    <button @click="handleClick('title')"> title</button>
    <button @click="handleClick('salary')"> salary</button>
    <button @click="handleClick('location')"> location</button>
    <JobList :jobs="jobs"  :order="order" />
  </div>
</template>

<script lang="ts">
import { defineComponent, reactive, ref, toRefs } from "vue";
import JobList from './components/JobsList.vue'
import TOrderTerm from './types/OrderTerm'
import IJob from "./types/Job";

export default defineComponent({
  name: "App",

  components: {JobList},

  setup() {
    const jobs = ref<IJob[]>([
      { title: "Fermier", location: "Samoens", salary: 30000, id: "1" },
      { title: "Web developer", location: "Dijon", salary: 50000, id: "2" },
      { title: "Pharmacien", location: "Cluses", salary: 60000, id: "3" },
      { title: "Serveur", location: "Les Carroz", salary: 27000, id: "4" },
      { title: "Osthéopath", location: "Uriage", salary: 55000, id: "5" },
    ]);

    const order = ref<TOrderTerm>('title')

    const handleClick = (term: TOrderTerm) => {
      order.value = term
    }

    return {jobs, handleClick, order}
  },
  methods: {},
});
</script>
