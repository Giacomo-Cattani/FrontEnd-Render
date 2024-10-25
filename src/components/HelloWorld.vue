<script setup lang="ts">
import { ref, onMounted } from 'vue'
import axios from 'axios'

defineProps<{ msg: string }>()

const count = ref(0)
const data = ref(null)

onMounted(async () => {
  try {
    const response = await axios.get('https://backend-render-ocex.onrender.com')
    data.value = response.data
  } catch (error) {
    console.error('There was a problem with the axios operation:', error)
  }
})
</script>

<template>
  <h1>{{ msg }}</h1>

  <div class="card">
    <button type="button" @click="count++">count is {{ count }}</button>
    <p>
      Edit
      <code>components/HelloWorld.vue</code> to test HMR
    </p>
  </div>

  <p v-if="data">
    API Data: {{ data }}
    {{ !data ? "Problemi Axios" : "" }}
  </p>

  <p>
  </p>
</template>
