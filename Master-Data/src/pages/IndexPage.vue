<template>
  <div>
    <img src="/LogoV3.png" alt="">
    <div class="flex gap-20 justify-center items-center" style="height: 100vh;">
      <CreateUser/>
      <CreateProduct/>
      <CreateCustomer/>
      <CreateSupplier/>
      <CreatePayment/>
      <CreateExpenses/>
    </div>
  </div>
</template>

<script setup>
import CreateUser from 'src/components/dialog/CreateUser.vue';
import CreateProduct from 'src/components/dialog/CreateProduct.vue';
import CreateCustomer from 'src/components/dialog/CreateCustomer.vue';
import CreateSupplier from 'src/components/dialog/CreateSupplier.vue';
import CreatePayment from 'src/components/dialog/CreatePayment.vue';
import CreateExpenses from 'src/components/dialog/CreateExpenses.vue';

</script>
