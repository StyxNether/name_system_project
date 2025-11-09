<template>
  <div class="home">
    <h1>智能取名系统</h1>
    <NameForm @generate="handleGenerate" />
    <NameResult v-if="results" :results="results" />
  </div>
</template>

<script>
import NameForm from '@/components/NameForm.vue'
import NameResult from '@/components/NameResult.vue'

export default {
  components: {
    NameForm,
    NameResult
  },
  data() {
    return {
      results: null
    }
  },
  methods: {
    handleGenerate(results) {
      this.results = results
    }
  }
}
</script>