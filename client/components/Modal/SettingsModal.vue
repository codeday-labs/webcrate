<template>
  <Modal class="settings-modal" @close="close">
    <h1>Themes</h1>
    <div class="buttons">
      <input v-model="active" class="radio" type="radio" value="Light" @click="click('Light')" />
      <input v-model="active" class="radio" type="radio" value="Dark" @click="click('Dark')" />
      <input v-model="active" class="radio" type="radio" value="Other" @click="click('Other')" />
    </div>
  </Modal>
</template>

<script>
export default {
	data() {
		return {
			active: 'Light'
		}
	},
	setTheme(newTheme): {
		nextClass = ['theme-', newTheme].join('')
		prevClass = ['theme-', this.active].join('')
		document.documentElement.setAttribute('data-theme', newTheme)
		document.body.classList.add(nextClass)
		document.body.classList.remove(prevClass)
		this.active = newTheme
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
		click(clicked) {
			if (!(this.active === clicked)) {
				this.isDark = this.$darkmode.toggle()
			}
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