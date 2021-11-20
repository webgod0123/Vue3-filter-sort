<template>
  <div class="row">
    <filterbar
      :filterOptions="filterOptions"
      @changeSort="changeSort($event)"
      @changeFilter="changeFilter($event)"
      @changeSearchVal="setSearchVal($event)"
    />
    <lessons :lessons="filteredLessons" />
  </div>
</template>

<script>
import Filterbar from "../components/Filterbar.vue";
import Lessons from "../components/Lessons.vue";
import lessonsData from "../data/lessons.json";

export default {
  components: {
    Filterbar,
    Lessons,
  },
  data() {
    return {
      lessons: lessonsData.lessons,
      filterOptions: {
        sort: "subject",
        filter: "ascending",
      },
      searchVal: "",
      filteredLessons: [],
    };
  },
  mounted() {
    this.filterLessons(this.filterOptions.sort, this.filterOptions.filter);
  },
  methods: {
    changeSort(sort) {
      this.filterOptions.sort = sort;
      this.filterLessons(this.filterOptions.sort, this.filterOptions.filter);
    },
    changeFilter(filter) {
      this.filterOptions.filter = filter;
      this.filterLessons(this.filterOptions.sort, this.filterOptions.filter);
    },
    filterLessons(sort, filter) {
      let filterLessons = this.lessons;
      filterLessons = filterLessons.sort((a, b) => {
        let fa = a[sort],
          fb = b[sort];
        if (filter == "ascending") {
          if (fa < fb) {
            return -1;
          }
          if (fa > fb) {
            return 1;
          }
          return 0;
        } else {
          if (fa > fb) {
            return -1;
          }
          if (fa < fb) {
            return 1;
          }
          return 0;
        }
      });
      this.filteredLessons = filterLessons;
      this.lessons = filterLessons;
    },
    setSearchVal(val) {
      this.searchVal = val;
      this.filteredLessons = this.searchLessons(this.lessons);
    },
    searchLessons(lessons) {
      return lessons.filter(
        (lesson) =>
          lesson.subject
            .toString()
            .toLowerCase()
            .includes(this.searchVal.toLowerCase()) ||
          lesson.location
            .toString()
            .toLowerCase()
            .includes(this.searchVal.toLowerCase()) ||
          lesson.price
            .toString()
            .toLowerCase()
            .includes(this.searchVal.toLowerCase()) ||
          lesson.space
            .toString()
            .toLowerCase()
            .includes(this.searchVal.toLowerCase())
      );
    },
  },
};
</script>
