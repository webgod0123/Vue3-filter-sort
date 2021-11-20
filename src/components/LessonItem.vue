<template>
  <div class="col-md-4 col-lg-3 col-sm-6 mb-4">
    <div class="rounded-3 shadow-lg p-3 bg-white">
      <div class="row">
        <div class="col-xl-7 col-md-12 col-sm-7">
          <div>
            <small>
              <span class="fw-bold">Subject: </span>{{ lesson.subject }}
            </small>
          </div>
          <div>
            <small>
              <span class="fw-bold">Location: </span>{{ lesson.location }}
            </small>
          </div>
          <div>
            <small>
              <span class="fw-bold">Price: </span>£ {{ lesson.price }}
            </small>
          </div>
          <div>
            <small>
              <span class="fw-bold">Spaces: </span>{{ lesson.space }}
            </small>
          </div>
        </div>
        <div class="col-xl-5 col-md-12 col-sm-5 p-4 p-sm-0 p-md-4 p-xl-0">
          <img
            :src="require(`@/assets/images/${lesson.image}`)"
            class="w-100"
          />
        </div>
      </div>
      <button class="btn btn-primary mt-4 form-control">Add to Cart</button>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    lesson: Object,
  },
};
</script>
