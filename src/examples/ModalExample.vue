<template lang="html">
  <div class="container">
    <h1>Modal Example</h1>
    <row>
      <div class="col-md-12">
        <!-- Button trigger modal -->
        <button type="button" class="btn btn-primary btn-lg" @click="openModal">
          Launch demo modal
        </button>
      </div>
    </row>
  </div>
</template>

<script>
export default {
  methods: {
    openModal () {
      console.log(this.$bus)
      this.$bus.$emit('modal-open', {
        title: 'Hello',
        description: '内容',
        type: 'modal-primary',
        confirmText: '保存并关闭',
        cancelText: '关闭',
        confirmBefore: () => {
          window.alert('保存后关闭前钩子函数')
        },
        confirmAfter: () => {
          window.alert('保存后关闭后钩子函数')
        },
        cancelBefore: () => {
          window.alert('关闭前钩')
        },
        cancelAfter: () => {
          window.alert('关闭后钩子函数')
        }
      })
    }
  }
}
</script>

<style lang="css" scoped>
.modal-example .modal {
  position: relative;
  top: auto;
  bottom: auto;
  right: auto;
  left: auto;
  display: block;
  z-index: 1;
}
.modal-example .modal {
  background: transparent !important;
}
</style>
