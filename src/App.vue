<template>
  <div id="app">
		<div class="wrap">
			<div>
				<drag-and-drop-modules
						:type-kitchen="typeKitchen"
						:fridge="fridge"
				/>
			</div>
			<div class="options__block">
				<span>Choose type of kitchen</span>
				<div
						v-for="(item) of types"
						:key="item"
						class="options__item"
				>
				<input
						type="radio"
						:value="item"
						:checked="item.toLowerCase() === typeKitchen"
						@change="changeTypeKitchen(item)"
				/>
				<label>{{ item }}</label>
				</div>
				<span>Choose fridge position</span>
				<div
						v-for="(item) of fridgePositions"
						:key="item"
						class="options__item"
				>
					<input
							type="radio"
							:value="item"
							:checked="item.toLowerCase() === fridge"
							@change="changeFridgePosition(item)"
					/>
					<label>{{ item }}</label>
				</div>
			</div>
		</div>
	</div>
</template>

<script>

import DragAndDropModules from "@/components/DragAndDropModules";

export default {
  name: 'App',
  components: {DragAndDropModules},
	data: () => ({
		typeKitchen: 'straight',
		fridge: 'no',
		fridgePositions: ['Left', 'Right', 'No'],
		types: ['Straight', 'Corner']
	}),
	methods: {
		changeTypeKitchen(value) {
			// eslint-disable-next-line no-mixed-spaces-and-tabs
			this.typeKitchen = value.toLowerCase()
			localStorage.clear()
		},
		changeFridgePosition(value) {
			this.fridge = value.toLowerCase()
			localStorage.clear()
		}
	}
}
</script>

<style>
.wrap {
	display: flex;
	flex-direction: column-reverse;
}
.options__block {
	border: 1px solid grey;
	border-radius: 3px;
	padding: 15px 5px;
	background-color: #f5f5f5;
	width: 40%;
}
</style>
