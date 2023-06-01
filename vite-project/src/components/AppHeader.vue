<template>
  <header>
    <h1 :style="{ color: color }"><slot>No Title</slot></h1>
  </header>
</template>

<script setup>
defineProps(["color"]);
</script>
