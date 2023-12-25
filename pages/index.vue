<template>
    <div>

        <div class="flex min-h-screen bg-gray-100 dark:bg-gray-900">
            <div class="w-64 bg-white dark:bg-gray-800 flex flex-col">
                <h1 class="text-3xl font-bold p-2">Nuxt Chat App</h1>
                <div class="p-6 flex-grow">
                    <h2 class="text-xl font-bold">Chats</h2>
                    <nav class="mt-6 space-y-1">
                        <a class="flex items-center px-3 py-2 rounded-md text-gray-600 hover:bg-gray-200 dark:text-gray-400 dark:hover:bg-gray-700"
                            href="#">
                            Chat 1
                        </a>
                        <a class="flex items-center px-3 py-2 rounded-md text-gray-600 hover:bg-gray-200 dark:text-gray-400 dark:hover:bg-gray-700"
                            href="#">
                            Chat 2
                        </a>
                        <a class="flex items-center px-3 py-2 rounded-md text-gray-600 hover:bg-gray-200 dark:text-gray-400 dark:hover:bg-gray-700"
                            href="#">
                            Chat 3
                        </a>
                    </nav>
                </div>
                <div class="p-6 border-t">
                    <button
                        class="inline-flex items-center justify-center rounded-md text-sm font-medium ring-offset-background transition-colors focus-visible:outline-none focus-visible:ring-2 focus-visible:ring-ring focus-visible:ring-offset-2 disabled:pointer-events-none disabled:opacity-50 bg-primary text-primary-foreground hover:bg-primary/90 h-10 px-4 py-2 mb-2 w-full">
                        Settings
                    </button>
                    <button
                        class="inline-flex items-center justify-center rounded-md text-sm font-medium ring-offset-background transition-colors focus-visible:outline-none focus-visible:ring-2 focus-visible:ring-ring focus-visible:ring-offset-2 disabled:pointer-events-none disabled:opacity-50 bg-primary text-primary-foreground hover:bg-primary/90 h-10 px-4 py-2 mb-2 w-full">
                        Help
                    </button>
                    <button
                        class="inline-flex items-center justify-center rounded-md text-sm font-medium ring-offset-background transition-colors focus-visible:outline-none focus-visible:ring-2 focus-visible:ring-ring focus-visible:ring-offset-2 disabled:pointer-events-none disabled:opacity-50 bg-primary text-primary-foreground hover:bg-primary/90 h-10 px-4 py-2 w-full">
                        Connect to Server
                    </button>
                </div>
            </div>
            <div class="flex-1 flex flex-col">
                <div class="flex-1 overflow-y-auto p-6">
                    <div class="mb-4">
                        <div class="flex items-start space-x-2">
                            <span class="relative flex h-10 w-10 shrink-0 overflow-hidden rounded-full" alt="User 1"
                                src="/placeholder.svg?height=32&amp;width=32"></span>
                            <div>
                                <div class="font-medium">User 1</div>
                                <div class="text-sm text-gray-500 dark:text-gray-400">2:12 PM</div>
                            </div>
                        </div>
                        <div class="mt-2 bg-gray-200 dark:bg-gray-800 rounded-md p-2">Hello!</div>
                    </div>
                    <div class="mb-4">
                        <div class="flex items-start justify-end space-x-2">
                            <div>
                                <div class="font-medium">User 2</div>
                                <div class="text-sm text-gray-500 dark:text-gray-400">2:14 PM</div>
                            </div>
                            <span class="relative flex h-10 w-10 shrink-0 overflow-hidden rounded-full" alt="User 2"
                                src="/placeholder.svg?height=32&amp;width=32"></span>
                        </div>
                        <div class="mt-2 bg-gray-200 dark:bg-gray-800 rounded-md p-2 text-right">
                            Hi there! How can I assist you today?
                        </div>
                    </div>
                </div>
                <div class="border-t">
                    <div class="flex items-center space-x-4 p-6">
                        <textarea
                            class="flex w-full rounded-md border border-input px-3 py-2 text-sm ring-offset-background placeholder:text-muted-foreground focus-visible:outline-none focus-visible:ring-2 focus-visible:ring-ring focus-visible:ring-offset-2 disabled:cursor-not-allowed disabled:opacity-50 flex-1 min-h-[20px] bg-white dark:bg-gray-800"
                            id="message" placeholder="Type your message"></textarea>
                        <button
                            class="inline-flex items-center justify-center rounded-md text-sm font-medium ring-offset-background transition-colors focus-visible:outline-none focus-visible:ring-2 focus-visible:ring-ring focus-visible:ring-offset-2 disabled:pointer-events-none disabled:opacity-50 bg-primary text-primary-foreground hover:bg-primary/90 h-10 px-4 py-2">
                            Send
                        </button>
                    </div>
                </div>
            </div>
            <div class="w-64 bg-white dark:bg-gray-800">
                <div class="p-6">
                    <h2 class="text-xl font-bold">Chat Configuration</h2>
                    <div class="mt-6">
                        <div class="flex items-center justify-between">
                            <label class="flex-1" for="darkMode">
                                Dark Mode
                            </label>
                            <input class="text-gray-600 dark:text-gray-400" id="darkMode" type="checkbox" />
                        </div>
                        <div class="flex items-center justify-between mt-4">
                            <label class="flex-1" for="notifications">
                                Notifications
                            </label>
                            <input class="text-gray-600 dark:text-gray-400" id="notifications" type="checkbox" />
                        </div>
                        <div class="flex items-center justify-between mt-4">
                            <label class="flex-1" for="sounds">
                                Sounds
                            </label>
                            <input class="text-gray-600 dark:text-gray-400" id="sounds" type="checkbox" />
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>

<script setup lang="ts">
const client = useSupabaseClient()

const { data: restaurant } = await useAsyncData('restaurant', async () => {
    const { data } = await client.from('restaurants').select('name, location').eq('name', 'My Restaurant Name').single()

    return data
})
</script>

<style scoped></style>