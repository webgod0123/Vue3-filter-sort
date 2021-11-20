<template>
  <div class="col-md-10">
    <div class="row">
      <lesson-item
        v-for="(lesson, index) in lessons"
        :key="index"
        :lesson="lesson"
      />
    </div>
  </div>
</template>

<script>
import LessonItem from "./LessonItem.vue";

export default {
  props: {
    lessons: Array,
  },
  components: {
    LessonItem,
  },
};
</script>
