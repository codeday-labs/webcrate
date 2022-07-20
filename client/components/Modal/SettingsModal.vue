<template>
  <Modal class="settings-modal" @close="close">
    <h1>Settings</h1>
    <div class="buttons">
      <button class="button">
        <Icon name="sun" />Themes
      </button>
      <button class="button">
        <Icon name="code" />Other
      </button>
      <button class="button">
        <Icon name="code" />Other
      </button>
    </div>
  </Modal>
</template>

<script>
export default {
	data() {
		return {}
	},
	computed: {
		currentSetting: {
			set(value) {
				this.$store.commit('SET_CURRENT_SETTING', value)
			},
			get() {
				return this.$store.state.currentSetting
			}
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
	& button {
			display: flex;
			align-items: center;
			margin-top: 0.7rem;

			& div {
				margin-right: 0.3rem;
				margin-left: -3px;
			}
		}
  }
</style>