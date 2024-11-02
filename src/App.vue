<template>
  <main class="flex h-screen w-full">
    <Channels :selectedChannel />
    <Chat :selectedChannel />
    <Users />
  </main>
</template>

<script setup lang="ts">
import Channels from '@/components/channels/Channels.vue'
import Chat from '@/components/chat/Chat.vue'
import Users from '@/components/users/Users.vue'
import { ref } from 'vue'

const selectedChannel = ref(1)
</script>
