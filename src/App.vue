<script setup>
import {ref, reactive} from 'vue'
import WatchComponent from "./components/WatchComponent.vue"
import ComputeComponent from "./components/ComputeComponent.vue"

const selectedComponent = ref('computed')
</script>
<template>
	<div class="flex justify-center">
		<div class=" w-full md:w-400 bg-blue-300 p-4">
			<div class="flex justify-center">
				<!-- <div class="text-center bg-blue-500 px-4 py-2 rounded-l-lg border-r border-white hover:bg-blue-700" :class="[$route.name == 'todo' ? 'bg-blue-700' : '']">Todo App</div> -->
				<div @click="selectedComponent = 'computed'" class="w-52 cursor-pointer text-center bg-blue-500 px-4 py-2 rounded-l-lg border-r border-white hover:bg-blue-700" :class="[selectedComponent == 'computed' ? 'bg-blue-700' : '']">Computed</div>

				<!-- <div class="text-center bg-blue-500 px-4 py-2 rounded-r-lg hover:bg-blue-700" :class="[$route.name != 'todo' ? 'bg-blue-700' : '']">Auth App</div> -->
				<div @click="selectedComponent = 'watch'" class="w-52 cursor-pointer text-center bg-blue-500 px-4 py-2 rounded-r-lg hover:bg-blue-700" :class="[selectedComponent == 'watch' ? 'bg-blue-700' : '']">Watch</div>
			</div>
		</div>
	</div>
	
	<WatchComponent v-if="selectedComponent == 'watch'"/>
	<ComputeComponent v-if="selectedComponent == 'computed'"/>
</template>