<template>
  <div class="col-md-2 mb-4">
    <div class="form-group">
      <input
        type="text"
        class="form-control"
        placeholder="Search here..."
        @keyup="changeSearchVal"
      />
    </div>
    <div class="mt-4">
      <h5>Sort By</h5>
      <div class="form-group">
        <input
          type="radio"
          class="form-check-input"
          id="subject"
          name="sort"
          value="subject"
          v-model="sort"
          @change="changeSort"
        />
        <label class="ms-2" for="subject">Subject</label>
      </div>
      <div class="form-group">
        <input
          type="radio"
          class="form-check-input"
          id="location"
          name="sort"
          value="location"
          v-model="sort"
          @change="changeSort"
        />
        <label class="ms-2" for="location">Location</label>
      </div>
      <div class="form-group">
        <input
          type="radio"
          class="form-check-input"
          id="price"
          name="sort"
          value="price"
          v-model="sort"
          @change="changeSort"
        />
        <label class="ms-2" for="price">Price</label>
      </div>
      <div class="form-group">
        <input
          type="radio"
          class="form-check-input"
          id="availability"
          name="sort"
          value="space"
          v-model="sort"
          @change="changeSort"
        />
        <label class="ms-2" for="availability">Availability</label>
      </div>
      <div class="mt-4">
        <div class="form-group">
          <input
            type="radio"
            class="form-check-input"
            id="ascending"
            name="filter"
            v-model="filter"
            value="ascending"
            @change="changeFilter"
          />
          <label class="ms-2" for="ascending">Ascending</label>
        </div>
        <div class="form-group">
          <input
            type="radio"
            class="form-check-input"
            id="descending"
            name="filter"
            v-model="filter"
            value="descending"
            @change="changeFilter"
          />
          <label class="ms-2" for="descending">Descending</label>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    filterOptions: Object,
  },
  data() {
    return {
      sort: this.filterOptions.sort,
      filter: this.filterOptions.filter,
    };
  },
  methods: {
    changeSort(e) {
      this.$emit("changeSort", e.target.value);
    },
    changeFilter(e) {
      this.$emit("changeFilter", e.target.value);
    },
    changeSearchVal(e) {
      this.$emit("changeSearchVal", e.target.value);
    },
  },
};
</script>
