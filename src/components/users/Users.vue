<template>
  <aside class="w-1/6 border-l-2 border-black p-5">
    <p>Users ({{ users.length }})</p>
    <ul class="mt-4">
      <li v-for="(user, key) in users" :key="key">
        {{ user.username }}
      </li>
    </ul>
  </aside>
</template>

<script setup lang="ts">
import { defineComponent } from 'vue'
import { users } from '@/data/users.json'

defineComponent({ name: 'Users' })
</script>
