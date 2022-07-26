<template>
  <Modal class="settings-modal" @close="close">
    <h1>Themes</h1>
    <div class="container">
      <div class="themes">
        Current theme: {{ activeTheme }}
        <input v-model="activeTheme" class="radio" type="radio" value="light" @click="setTheme('light')" />
        <input v-model="activeTheme" class="radio" type="radio" value="dark" @click="setTheme('dark')" />
        <input v-model="activeTheme" class="radio" type="radio" value="other" @click="setTheme('other')" />
      </div>
      <div class="customise">
      </div>
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
			const nextClass = [ 'theme-', newTheme ].join('')
			const prevClass = [ 'theme-', this.activeTheme ].join('')
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

	.themes {
		width: 60%;
		border-right: 2px solid black;
	}
	.customise {
		margin-left: 0.7rem;
		width: 60%;
	}

	.container {
		display: flex;
		align-items: flex-start;
	}
  }

</style>