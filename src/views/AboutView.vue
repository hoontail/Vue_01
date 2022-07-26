<template>
  <div class="about">
    <h1>This is an about page</h1>
    <Practice/>
  </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue'
import Practice from '@/components/Practice.vue' // @ is an alias to /src

export default defineComponent({
  name: 'HomeView',
  components: {
    Practice
  }
})
</script>
