<script lang="ts" setup>
const { modelUsed } = useConversations()

const options = [
    { value: 'gpt-3.5-turbo', label: 'GPT 3.5', icon: 'i-tabler-brand-openai' },
    { value: 'gpt-4', label: 'GPT 4', icon: 'i-tabler-brand-openai' },
] as const

function onClick(model: string) {
    modelUsed.value = model
}
</script>

<template>
    <div>
        <div font-bold text-gray-6 dark:text-gray-3 mb-3>
            Model
        </div>
        <div flex gap-3>
            <div
                v-for="option in options"
                :key="option.value"
                grow flex flex-col items-center p-2
                rounded-2 ring-1
                cursor-pointer
                class="dark:ring-white/10 ring-gray-2"
                text-gray-5
                dark:text-gray-3 gap-2
                :class="[
                    modelUsed === option.value ? '!ring-primary-400 !dark:ring-primary-400 ring-2 !text-primary' : '',
                ]"
                @click="onClick(option.value)"
            >
                <div :class="option.icon" text-6 />
                <div>{{ option.label }}</div>
            </div>
        </div>
    </div>
</template>
