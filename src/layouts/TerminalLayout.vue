<template>
  <div class="min-h-screen flex flex-col font-mono text-[var(--color-primary)]">
    <!-- Header -->
    <header class="p-4 border-b-2 border-[var(--color-primary)] flex justify-between items-center bg-black sticky top-0 z-50">
      <div class="flex items-center gap-4">
        <div class="w-10 h-10 border-2 border-[var(--color-primary)] flex items-center justify-center rounded-sm">
          <span class="text-2xl font-bold">[]</span>
        </div>
        <h1 class="text-xl font-bold tracking-wider terminal-glow">MUSIC_SHOWCASE.EXE</h1>
      </div>
      
      <button class="text-[var(--color-primary)] focus:outline-none md:hidden">
        <span class="text-3xl">≡</span>
      </button>

      <nav class="hidden md:flex gap-6">
        <RouterLink to="/" class="hover:underline hover:text-white transition-colors">ROOT</RouterLink>
        <RouterLink to="/login" class="hover:underline hover:text-white transition-colors">LOGIN</RouterLink>
        <a href="#" class="hover:underline hover:text-white transition-colors">SYSTEM</a>
        <a href="#" class="hover:underline hover:text-white transition-colors">LOGS</a>
      </nav>
    </header>

    <!-- Main Content -->
    <main class="flex-1 p-4 md:p-8 container mx-auto">
      <slot></slot>
    </main>

    <!-- Footer -->
    <footer class="p-4 border-t border-[var(--color-primary)] text-center text-xs opacity-50">
      <p>SYSTEM STATUS: ONLINE | V.1.0.0</p>
    </footer>
  </div>
</template>
