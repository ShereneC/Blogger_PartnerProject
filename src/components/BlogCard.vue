<template>
  <div class="col-11 my-3 bg-light shadow">
    <div class="" data-toggle="modal" :data-target="'#blog-modal-'+blog.id">
      <h3>{{ blog.title }}</h3>
      <p>{{ blog.body }}</p>
      <div class="align-self-end" v-if="account.id === blog.creatorId">
        <button class="btn btn-danger" @click.stop="destroy">
          delete
        </button>
      </div>
      <div>
        <router-link router-link :to="{ name: 'Profile', params: {id: blog.creator.id } }" @click.stop="" class="creator p-3 align-self-end">
          <img class="h-100 rounded-pill" :src="blog.creator.picture" alt="" srcset="">
          {{ blog.creator.name }}
        </router-link>
      </div>
    </div>
  </div>
  <BlogModal :blog="blog" />
</template>

<script>
import { computed } from '@vue/runtime-core'
import { AppState } from '../AppState'
import Pop from '../utils/Notifier'
import { blogsService } from '../services/BlogsService'

export default {
  props: {
    blog: {
      type: Object,
      required: true
    }
  },
  setup(props) {
    return {
      account: computed(() => AppState.account),
      async destroy() {
        try {
          if (await Pop.confirm()) {
            await blogsService.destroy(props.blog.id)
            Pop.toast('Delorted', 'success')
          }
        } catch (error) {
          Pop.toast(error, 'error')
        }
      }
    }
  }

}
</script>

<style lang="scss" scoped>

.image-size {
  height: 30px;
  width: 30px;
  border-radius: 50%
}
</style>
