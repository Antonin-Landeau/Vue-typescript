<template>
  <div>
    <p>Ordered by : {{order}}</p>
    <ul>
      <li v-for="job in orderedJobs" :key="job.id">
        <h2>{{ job.title }} in {{ job.location }}</h2>
        <div>{{ job.salary }} €</div>
        <p>
          Lorem ipsum dolor sit amet consectetur adipisicing elit. Temporibus,
          sunt excepturi id maiores itaque reprehenderit!
        </p>
      </li>
    </ul>
  </div>
</template>
<script lang="ts">
import { computed, defineComponent, PropType } from "vue";
import TOrderTerm from '@/types/OrderTerm'
import IJob from "@/types/Job";

export default defineComponent({
  props: {
    jobs: {
      required: true,
      type: Array as PropType<IJob[]>,
    },
    order: {
      required: true,
      type: String as PropType<TOrderTerm>,
    }
  },
  setup(props) {
    const orderedJobs = computed(() => {
      return [...props.jobs].sort((a:IJob ,b :IJob) => {
        return a[props.order] > b[props.order] ? 1 : -1
      })
    })

    return {orderedJobs}
  }
});
</script>

<style scoped></style>
>
