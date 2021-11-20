<template>
  <div>
    <navbar />
    <div class="container-fluid py-4">
      <router-view></router-view>
    </div>
  </div>
</template>

<script>
import Navbar from "@/components/Navbar.vue";

export default {
  components: {
    Navbar
  }
}
</script>
