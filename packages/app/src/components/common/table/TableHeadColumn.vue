<template>
  <th scope="col" class="table-head-col">
    <slot></slot>
  </th>
</template>

<script setup lang="ts"></script>

<style>
.table-head-col {
  @apply whitespace-nowrap px-2 py-3 text-left text-xs font-light uppercase tracking-wider text-silver-500 first:pl-6 last:pr-6;
}
</style>
