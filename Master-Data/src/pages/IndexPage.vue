<template>
  <div class="bg-gradient-to-tl from-blue-400 to to-blue-950 p-10">
    <div class="flex gap-20 justify-center items-center" style="height: 100vh;">
      <CreateUser/>
      <CreateProduct/>
      <CreateCustomer/>
      <CreateSupplier/>
      <CreatePayment/>
      <CreateExpenses/>
    </div>
  </div>
  <!-- <img class="image" src="../assets/LogoV3.jpg" alt="" width="100vh"> -->
</template>

<script setup>
import CreateUser from 'src/components/dialog/CreateUser.vue';
import CreateProduct from 'src/components/dialog/CreateProduct.vue';
import CreateCustomer from 'src/components/dialog/CreateCustomer.vue';
import CreateSupplier from 'src/components/dialog/CreateSupplier.vue';
import CreatePayment from 'src/components/dialog/CreatePayment.vue';
import CreateExpenses from 'src/components/dialog/CreateExpenses.vue';

</script>
<style scoped>
.image{
  position: absolute;
  top: 0;
  z-index: 0;
}
</style>
