<template>
  <div
    data-iframe-height
    class="text-caption"
  >
    This is a frame that updates its own query parameters and reacts to dynamic changes from the parent.
    <br>
    It exposes a vue router in window.vIframeOptions.router.
    <br>
    param1={{ param1 }}
    <br>
    param2={{ param2 }}
    <br>
    <v-btn
      color="primary"
      variant="elevated"
      @click="param1 += 1"
    >
      Increment 1
    </v-btn>
    <v-btn
      color="primary"
      variant="elevated"
      class="ml-2"
      @click="param1 = 0"
    >
      Clear 1
    </v-btn>
    <br>
    <v-btn
      color="primary"
      variant="elevated"
      class="mt-2"
      @click="param2 += 1"
    >
      Increment 2
    </v-btn>
    <v-btn
      color="primary"
      variant="elevated"
      class="ml-2 mt-2"
      @click="param2 = 0"
    >
      Clear 2
    </v-btn>
    <br>
    <source-link class="mt-4" />
  </div>
</template>

<script setup lang="ts">
import '../../../lib/v-iframe-compat/d-frame-content'
import type { VIframeOptions } from '../../../lib/v-iframe-compat/d-frame-content'

const router = useRouter()
const route = useRoute();

(window as (Window & { vIframeOptions?: VIframeOptions })).vIframeOptions = { router }

const param1 = computed({
  get() {
    return Number(route.query.param1 ?? 0)
  },
  set(value: number) {
    router.replace({ query: { ...route.query, param1: value || undefined } })
  },
})
const param2 = computed({
  get() {
    return Number(route.query.param2 ?? 0)
  },
  set(value: number) {
    router.replace({ query: { ...route.query, param2: value || undefined } })
  },
})
</script>
