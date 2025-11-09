<template>
  <div class="name-form">
    <form @submit.prevent="submitForm">
      <div class="form-group">
        <label>姓氏：</label>
        <input v-model="formData.surname" required>
      </div>
      
      <div class="form-group">
        <label>性别：</label>
        <select v-model="formData.gender">
          <option value="男">男</option>
          <option value="女">女</option>
          <option value="未知">未知</option>
        </select>
      </div>
      
      <div class="form-group">
        <label>出生日期：</label>
        <input type="date" v-model="formData.birthday">
      </div>
      
      <div class="form-group">
        <label>出生时辰：</label>
        <select v-model="formData.birthTime">
          <option value="子时">子时 (23:00-01:00)</option>
          <option value="丑时">丑时 (01:00-03:00)</option>
          <!-- 添加其他时辰 -->
        </select>
      </div>
      
      <div class="form-group">
        <label>期望寓意：</label>
        <textarea v-model="formData.expectation" placeholder="请输入对名字的期望，如：聪明、健康、有才华等"></textarea>
      </div>
      
      <button type="submit" :disabled="loading">
        {{ loading ? '生成中...' : '生成名字' }}
      </button>
    </form>
  </div>
</template>

<script>
export default {
  data() {
    return {
      formData: {
        surname: '',
        gender: '未知',
        birthday: '',
        birthTime: '',
        expectation: ''
      },
      loading: false
    }
  },
  methods: {
    async submitForm() {
      this.loading = true
      try {
        // 暂时模拟数据，明天连接后端
        const mockResults = {
          names: [
            { name: '测试名', meaning: '这是一个测试名字', explanation: '测试说明' }
          ]
        }
        this.$emit('generate', mockResults)
      } catch (error) {
        console.error('生成名字失败:', error)
      } finally {
        this.loading = false
      }
    }
  }
}
</script>