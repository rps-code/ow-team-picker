<template>
    <main class="block max-w-xl p-6 rounded-lg shadow bg-slate-800">
        <GitHub />

        <h5 class="mb-2 text-2xl font-bold tracking-tight text-white">OW Team Picker</h5>
        <p class="font-normal text-gray-400 mb-5">A simple tool to allow you to build your perfect team.</p>

        <div class="checkboxes flex flex-col">
            <label class="inline-flex items-center cursor-pointer my-1" v-for="(item, index) in checkboxes" :key="index">
                <input
                    type="checkbox"
                    :value="item.value"
                    v-model="selectedCheckboxes"
                    @change="handleCheckboxChange"
                    class="sr-only peer"
                />
                <div
                    class="relative w-11 h-6 bg-gray-700 peer-focus:outline-none peer-focus:ring-4 peer-focus:ring-blue-800 rounded-full peer peer-checked:after:translate-x-full rtl:peer-checked:after:-translate-x-full peer-checked:after:border-white after:content-[''] after:absolute after:top-[2px] after:start-[2px] after:bg-white after:border-gray-300 after:border after:rounded-full after:h-5 after:w-5 after:transition-all border-gray-600 peer-checked:bg-blue-600"
                ></div>
                <span class="ms-3 text-sm font-medium text-gray-300">{{ item.label }}</span>
            </label>

            <label class="inline-flex items-center cursor-pointer my-1 hover:cursor-not-allowed">
                <input type="checkbox" disabled value="" class="sr-only peer" />
                <div
                    class="relative w-11 h-6 bg-gray-700 peer-focus:outline-none peer-focus:ring-4 peer-focus:ring-blue-800 rounded-full peer peer-checked:after:translate-x-full rtl:peer-checked:after:-translate-x-full peer-checked:after:border-white after:content-[''] after:absolute after:top-[2px] after:start-[2px] after:bg-white after:border-gray-300 after:border after:rounded-full after:h-5 after:w-5 after:transition-all border-gray-600 peer-checked:bg-blue-600"
                ></div>
                <span class="ms-3 text-sm font-medium text-gray-300">Communication</span>
            </label>
        </div>

        <p class="mt-5 text-sm text-right text-gray-500">
            <a href="https://discordapp.com/users/292432182557933588/">Created with ❤️ by <span class="underline">rps</span></a>
        </p>
    </main>
</template>

<script setup lang="ts">
    import { ref, watch } from 'vue'
    import GitHub from '@/components/GitHub.vue'

    const checkboxes = ref([
        { label: 'Good Tank', value: 'tank' },
        { label: 'Good Damage', value: 'damage' },
        { label: 'Good Support', value: 'support' }
    ])

    const selectedCheckboxes = ref([])

    const handleCheckboxChange = () => {
        if (selectedCheckboxes.value.length > 2) selectedCheckboxes.value.shift()
    }

    watch(selectedCheckboxes, newVal => {
        if (newVal.length > 2) selectedCheckboxes.value = newVal.slice(-2)
    })
</script>
