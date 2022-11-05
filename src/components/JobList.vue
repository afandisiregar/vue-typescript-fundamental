<template>
  <div class="job-list">
    Order by {{ order }}
    <ul>
      <li v-for="job in orderedJob" :key="job.id">
        <h2>{{ job.title }} in {{ job.location }}</h2>
        <div class="salary">
          <p>{{ job.salary }} rupee</p>
        </div>
        <div class="description">
          <p>
            Lorem ipsum dolor sit, amet consectetur adipisicing elit. Corrupti,
            dolor.
          </p>
        </div>
      </li>
    </ul>
  </div>
</template>

<script lang="ts">
import { computed, defineComponent, PropType } from "vue";
import Job from "@/types/Job";
import OrderTerm from "@/types/OrderTerm";

export default defineComponent({
  props: {
    jobs: {
      type: Array as PropType<Job[]>,
      required: true,
    },
    order: {
      type: String as PropType<OrderTerm>,
      required: true,
    },
  },
  setup(props) {
    const orderedJob = computed(() => {
      return [...props.jobs].sort((a: Job, b: Job) => {
        return a[props.order] > b[props.order] ? 1 : -1;
      });
    });

    return { orderedJob };
  },
});
</script>

<style scoped></style>
