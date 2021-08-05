<template>
  <div class="row justify-content-center">
    <BlogCard v-for="b in blogs" :key="b.id" :blog="b" />
  </div>
</template>

<script>
export default {
  name: 'Thread',
  props: {
    blogs: {
      type: Array,
      required: true
    }
  }
}
</script>
