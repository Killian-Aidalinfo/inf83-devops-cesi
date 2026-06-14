<template>
  <div class="civit-footer" v-if="$slidev.nav.currentPage > 1">
    <img src="/civilisationit-logo.svg" class="w-3.5 h-3.5" />
    <span class="logo">Civilisation<span class="it">IT</span></span>
    <span class="sep">·</span>
    <span>{{ $slidev.configs.title }}</span>
    <span class="page">{{ $slidev.nav.currentPage }}/{{ $slidev.nav.total }}</span>
  </div>
</template>

<script setup>
</script>
