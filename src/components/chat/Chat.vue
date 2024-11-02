<template>
  <div class="flex w-4/6 flex-col justify-between">
    <section class="p-5">
      <h1 class="text-2xl font-bold">#{{ channel?.name }}</h1>
      <ul class="mt-4">
        <li v-for="(message, key) in chatMessages" :key>
          {{ message.user?.username }}: {{ message.content }}
        </li>
      </ul>
    </section>
    <section class="flex items-center gap-x-2 p-5">
      <p class="border border-black px-4 py-2">{{ loggedUser.username }}</p>
      <input
        type="text"
        class="w-full border border-black px-4 py-2"
        placeholder="Say something"
      />
      <button
        class="border border-black bg-black px-4 py-2 text-white underline-offset-2 hover:bg-neutral-800 hover:underline"
      >
        Send
      </button>
    </section>
  </div>
</template>

<script setup lang="ts">
import { defineComponent } from 'vue'
import { channels } from '@/data/channels.json'
import { messages } from '@/data/messages.json'
import { users } from '@/data/users.json'

type Props = {
  selectedChannel: number
}

defineComponent({ name: 'Chat' })

const props = defineProps<Props>()

const channel = channels.find(channel => channel.id === props.selectedChannel)
const chatMessages = messages
  .filter(message => message.channelId === props.selectedChannel)
  .map(message => ({
    ...message,
    user: users.find(user => user.id === message.userId)
  }))
const loggedUser = users[0]
</script>
