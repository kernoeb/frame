<template>
  <v-card
    variant="outlined"
    color="primary"
  >
    <v-card-text class="text-caption">
      This is a frame with a dynamic height and an offset.
      <div :style="`height:${height}px;`" />
      <v-btn
        color="primary"
        variant="elevated"
        class="mt-4"
        data-iframe-height="60"
        @click="height += 50"
      >
        Add 50px
      </v-btn>
      <br>
      <source-link class="mt-4" />
    </v-card-text>
  </v-card>
</template>

<script setup lang="ts">
import '../../../lib/d-frame-content'

const height = ref(0)
</script>
