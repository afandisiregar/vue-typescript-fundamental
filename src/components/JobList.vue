<template>
  <div class="job-list">
    <ul>
      <li v-for="job in jobs" :key="job.id">
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
import { defineComponent, PropType } from "vue";
import Job from "@/types/job";

export default defineComponent({
  props: {
    jobs: {
      type: Array as PropType<Job[]>,
      required: true,
    },
  },
});
</script>

<style scoped></style>
