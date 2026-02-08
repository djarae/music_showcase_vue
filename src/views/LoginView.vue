<template>
  <div class="max-w-md mx-auto mt-20">
    <TerminalCard>
      <div class="text-center mb-8">
        <h2 class="text-2xl font-bold mb-2 terminal-glow">AUTHENTICATION REQUIRED</h2>
        <p class="text-sm opacity-70">Please enter your credentials to access the system.</p>
      </div>

      <form @submit.prevent="handleLogin" class="space-y-6">
        <TerminalInput 
          v-model="username" 
          label="USERNAME" 
          placeholder="admin" 
        />
        
        <TerminalInput 
          v-model="password" 
          label="PASSWORD" 
          type="password" 
          placeholder="••••••" 
        />

        <div class="pt-4">
          <TerminalButton class="w-full">
            INITIALIZE SESSION
          </TerminalButton>
        </div>
      </form>

      <div class="mt-6 text-center text-xs opacity-50">
        <p>SECURE CONNECTION ESTABLISHED</p>
      </div>
    </TerminalCard>
  </div>
</template>

<script setup>
import { ref } from 'vue'
import { useRouter } from 'vue-router'
import TerminalInput from '../components/shared/TerminalInput.vue'
import TerminalButton from '../components/shared/TerminalButton.vue'
import TerminalCard from '../components/shared/TerminalCard.vue'

const router = useRouter()
const username = ref('')
const password = ref('')

const handleLogin = () => {
  // Mock login - just redirect
  console.log('Login attempt:', username.value)
  router.push('/')
}
</script>
