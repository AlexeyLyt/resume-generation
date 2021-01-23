<template>
  <form class="card card-w30" @submit.prevent>
      <div class="form-control">
        <label for="type">Тип блока</label>
        <select id="type" v-model="blockType">
          <option value="title">Заголовок</option>
          <option value="subtitle">Подзаголовок</option>
          <option value="avatar">Аватар</option>
          <option value="text">Текст</option>
        </select>
      </div>

      <div class="form-control">
        <label for="value">Значение</label>
        <textarea v-model="blockValue" id="value" rows="3"></textarea>
      </div>

      <button class="btn primary" :disabled="canAdd" @click="addBlock">Добавить</button>
    </form>
</template>

<script>
export default {
  emits: ['addBlock'],
  computed: {
    canAdd() {
      return this.blockValue.length < 3
    }
  },
  data: () => ({
    blockType: 'title',
    blockValue: ''
  }),
  methods: {
    addBlock() {
      this.$emit('addBlock', this.blockValue, this.blockType)
      this.blockValue = ''
      this.blockType = 'title'
    }
  }
}
</script>

<style>

</style>
