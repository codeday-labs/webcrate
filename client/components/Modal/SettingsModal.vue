<template>
  <Modal class="settings-modal" @close="close">
    <h1>Themes</h1>
    <div class="buttons">
      Current theme: {{activeTheme}}
      <input v-model="activeTheme" class="radio" type="radio" value="Light" @click="setTheme('light')" />
      <input v-model="activeTheme" class="radio" type="radio" value="Dark" @click="setTheme('dark')" />
      <input v-model="activeTheme" class="radio" type="radio" value="Other" @click="setTheme('other')" />
    </div>
  </Modal>
</template>

<script>
export default {
	data() {
		return {
			activeTheme: 'light'
		}
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
		},
		setTheme(newTheme) {
			const nextClass = ['theme-', newTheme].join('')
			const prevClass = ['theme-', this.activeTheme].join('')
			document.documentElement.setAttribute('data-theme', newTheme)
			document.body.classList.add(nextClass)
			document.body.classList.remove(prevClass)
			this.activeTheme = newTheme
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
	.radio {
		display: flex;
		align-items: center;
		margin-top: 0.7rem;
	}
  }

</style>