<template>
  <main>
    <ContentDoc v-slot="{ doc }">
      <h2 class="text-4xl font-semibold text-black dark:text-white">{{ doc.title }}</h2>
      <p class="text-gray-500 dark:text-white">
        by {{ doc.author }}, {{ doc.createdAt }}
      </p>
      <div class="max-w-4xl"
      >
        <ContentRenderer class="mt-4  max-w-none prose lg:prose-xl dark:prose-invert" :value="doc" />
      </div>
      <pre>
        {{ doc }}
      </pre>
      <div>
        <client-only>
          <Tui :modelValue="''"
            :get-html="()=>{}"
            :disabled="false"
            :loading="false"
          />
        </client-only>
      </div>
    </ContentDoc>
  </main>
</template>
<script setup lang="ts">
  const Tui = defineAsyncComponent(() => import('~/components/Tui.client.vue'));
</script>