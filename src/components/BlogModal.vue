<template>
  <!-- Modal -->
  <div class="modal"
       :id="'blog-modal-'+blog.id"
       tabindex="-1"
       role="dialog"
       aria-labelledby="modelTitleId"
       aria-hidden="true"
  >
    <div class="modal-dialog" role="document">
      <div class="modal-content">
        <div class="modal-header bg-dark">
          <h5 class="modal-title">
            {{ blog.title }}
          </h5>
          <button type="button" class="close text-light" data-dismiss="modal" aria-label="Close">
            <span aria-hidden="true">&times;</span>
          </button>
        </div>
        <div class="modal-body bg-dark">
          <div class="container-fluid">
            <p>{{ blog.body }}</p>
          </div>
        </div>
        <div class="modal-footer bg-dark">
          <button type="button" class="btn btn-secondary" data-dismiss="modal">
            Close
          </button>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    blog: {
      type: Object,
      required: true
    }
  },
  setup() {
    return {}
  }
}
</script>

<style lang="scss">
.modal-backdrop.show{
  opacity: 1!important;
  background:  var(--fade);
  backdrop-filter: blur(30px) brightness(.5) contrast(.85);
}

.modal-body{
  height: 50vh;
  overflow-y: auto;
}

.cover {
  object-fit: cover;
}
</style>
