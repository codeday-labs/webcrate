<template>
  <Modal class="settings-modal" @close="close">
    <h1>Settings</h1>
  </Modal>
</template>

<script>
export default {
	data() {
		return {
			name: undefined
		}
	},
	methods: {
		close() {
			this.$modal.hide()
		}
	}

}
</script>

<style lang="scss" scoped>
  .settings-modal {
    & h1 {
			font-size: 1.2rem;
			margin-bottom: 1rem;
		}
  }
</style>