<script setup>
import { computed, ref, watch } from 'vue';


const user = ref({
	name: "Al Nur Sarwer Arif",
	email: "alnurarif@yahoo.com",
	age: 33,
	img: "https://images.unsplash.com/photo-1526800544336-d04f0cbfd700?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=1974&q=80",
	birthYear: null,
	eligibleToVote: false,
})

watch(user, (newUser) => {
    const currentYear = new Date().getFullYear();
	user.value.birthYear = currentYear - newUser.age;

	user.value.eligibleToVote = user.value.age >= 18 ? "Eligible for voting" : "Not eligible for voting"
}, { deep: true, immediate: true })
</script>

<template>
<div class="max-w-md mx-auto mt-8 p-4">
    <h1 class="text-2xl font-semibold mb-4">User Details (Watch)</h1>
    <div class="flex justify-center">
        <img :src="user.img" class=" w-1/4 pr-5 pt-5 pb-5">
        <div class="w-3/4 p-5">
            <div class="mb-4">
                <label for="birthYear" class="block text-gray-600 text-sm">Birth Year: {{ user.birthYear }}</label>
            </div>
            <div>
                <label for="votingStatus" class="block text-gray-600  text-sm">Voting Status: {{ user.eligibleToVote }}</label>
            </div>
        </div>
    </div>
    <div class="mb-4">
        <label for="name" class="block text-gray-600">Name:</label>
        <input v-model="user.name" id="name" class="w-full border border-gray-300 rounded p-2" />
    </div>
    <div class="mb-4">
        <label for="email" class="block text-gray-600">Email:</label>
        <input v-model="user.email" id="email" type="email" class="w-full border border-gray-300 rounded p-2" />
    </div>
    <div class="mb-4">
        <label for="age" class="block text-gray-600">Age:</label>
        <input v-model.number="user.age" type="number" id="age" class="w-full border border-gray-300 rounded p-2" />
    </div>
    <div class="mb-4">
        <label for="img" class="block text-gray-600">Profile Img:</label>
        <input v-model="user.img" id="age" class="w-full border border-gray-300 rounded p-2" />
    </div>

</div>
</template>