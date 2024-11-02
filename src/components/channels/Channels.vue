<template>
  <aside class="w-1/6 border-r-2 border-black p-5">
    <p>Channels ({{ channels.length }})</p>
    <ul class="mt-4">
      <li
        v-for="(channel, key) in channels"
        :key
        class="cursor-pointer px-3 py-1 underline-offset-2"
        :class="
          channel.id === selectedChannel
            ? 'bg-black font-semibold text-white underline'
            : 'hover:bg-neutral-200 hover:underline'
        "
      >
        #{{ channel.name }}
      </li>
    </ul>
  </aside>
</template>

<script setup lang="ts">
import { defineComponent } from 'vue'
import { channels } from '@/data/channels.json'

type Props = {
  selectedChannel: number
}

defineComponent({ name: 'Channels' })

defineProps<Props>()
</script>
