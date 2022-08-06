<template>
	<div :class="$style.root">
		<div :class="$style.message">
			<img :class="$style.image" src="./assets/pub-golf-image.png" alt="">
			<div :class="$style.title">Pub Golf is going down in:</div>
			<div :class="$style.red">{{ days }} Days - {{ hours }} Hours - {{ minutes }} Minutes - {{ seconds }} Seconds</div>
		</div>
	</div>
</template>

<script>

export default {
	data() {
		return {
			days: null,
			hours: null,
			minutes: null,
			seconds: null,
		};
	},

	created() {
		const countDownDate = new Date('Aug 27, 2022 19:00:00').getTime();

		setInterval(() => {
			const now = new Date().getTime();

			const distance = countDownDate - now;

			this.days = Math.floor(distance / (1000 * 60 * 60 * 24));
			this.hours = Math.floor((distance % (1000 * 60 * 60 * 24)) / (1000 * 60 * 60));
			this.minutes = Math.floor((distance % (1000 * 60 * 60)) / (1000 * 60));
			this.seconds = Math.floor((distance % (1000 * 60)) / 1000);
		}, 1000);
	},
};
</script>

<style lang="scss" module>
	@import './styles/default';

	* {
		padding: 0;
		margin: 0;
		border: 0;
	}

	.root {
		display: flex;
		justify-content: center;
		align-items: center;
		height: 100vh;
		text-align: center;
	}

	.image {
		max-width: 100%;
		width: 50%;
	}

	.image,
	.title {
		margin-bottom: 12px;
	}

	.message {
		font-size: 2rem;
		color: black;
	}

	.red {
		color: red;
	}

	@media(max-width: 768px) {
		.message {
			font-size: 1.5rem;
		}

		.red {
			font-size: 1rem;
		}
	}
</style>
