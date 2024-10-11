<template>
  <div class="bg-slate-100">
    <div class="flex gap-20 justify-center items-center" style="height: 100vh;">
      <CreateUser/>
      <q-skeleton width="300px" height="200px"/>
      <q-skeleton width="300px" height="200px"/>
      <q-skeleton width="300px" height="200px"/>
      <q-skeleton width="300px" height="200px"/>
      <q-skeleton width="300px" height="200px"/>
    </div>
  </div>
</template>

<script setup>
import CreateUser from 'src/components/dialog/CreateUser.vue';
</script>
