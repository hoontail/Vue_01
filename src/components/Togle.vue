<template>
  <h1 v-if="isOpen">토글</h1>
  <button @click="toggle">{{ isOpen === true ? 'OFF' : 'ON' }}</button>
  <div id="hello">dd</div>
  <input :value="text" @input="onInput" />
</template>

<script lang="ts">
import { defineComponent } from 'vue'

export default defineComponent({
  name: 'BoardList',
  props: {},
  data: function () {
    return {
      text: '',
      isOpen: true
    }
  },
  methods: {
    onInput(e: any) {
      this.text = e.target.value
      console.log(this.text)
    },
    toggle() {
      this.isOpen = !this.isOpen
    }
  }
})
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped></style>
