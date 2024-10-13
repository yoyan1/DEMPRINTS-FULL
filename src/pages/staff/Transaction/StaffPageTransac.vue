<template>
  <div class="q-pa-md q-gutter-sm bg-white">
   
    <q-dialog v-model="lightDialog" persistent>
      <q-card style="width: 50%">
        <q-bar style="padding: 5%">
          <!-- <q-icon name="arrow_forward" /> -->
          <div>Add Transaction</div>

          <q-space />

          <q-btn dense flat icon="close" v-close-popup>
            <q-tooltip>Close</q-tooltip>
          </q-btn>
        </q-bar>

        <q-card-section>
          <q-form @submit="onSubmit" @reset="onReset" class="q-gutter-md">
            <q-input
              filled
              v-model="name"
              label="Your name *"
              hint="Name and surname"
              lazy-rules
              :rules="[
                (val) => (val && val.length > 0) || 'Please type something',
              ]"
            />

            <q-select v-model="model" label="Standard">
              <!-- <q-option></q-option> -->
            </q-select>

            <!-- <q-toggle v-model="accept" label="I accept the license and terms" /> -->

            <div>
              <q-btn label="Submit" type="submit" color="primary" />
              <q-btn
                label="Reset"
                type="reset"
                color="primary"
                flat
                class="q-ml-sm"
              />
            </div>
          </q-form>
        </q-card-section>
      </q-card>
    </q-dialog>

    <q-dialog
      v-model="darkDialog"
      persistent
      transition-show="flip-down"
      transition-hide="flip-up"
    >
      <q-card class="bg-primary text-white">
        <q-bar>
          <q-icon name="warning" />
          <div>Are you certain?</div>

          <q-space />

          <q-btn dense flat icon="close" v-close-popup>
            <q-tooltip class="bg-white text-primary">Close</q-tooltip>
          </q-btn>
        </q-bar>

        <q-card-section> hot </q-card-section>
      </q-card>
    </q-dialog>
  </div>

  <div class="q-pa-md">
   <q-btn @click="lightDialog = true" class="text-dark mb-3">
      <!-- <FontAwesomeIcon :icon="['fas', 'pen-to-square']" /> -->
      <span class="q-ml-sm">Add</span>
    </q-btn>

    <q-markup-table>
      <thead>
        <tr>
          <th class="text-left">Costumer Name</th>
          <th class="text-right">Type</th>
          <th class="text-right">Item</th>
          <th class="text-right">Quantity</th>
          <th class="text-right">Unit Cost</th>
          <th class="text-right">Amount</th>
        </tr>
      </thead>
      <tbody>
        <tr>
          <td class="text-left">Christian Mahinay</td>
          <td class="text-right">Walkin</td>
          <td class="text-right">Tarpulin</td>
          <td class="text-right">24</td>
          <td class="text-right">4</td>
          <td class="text-right">87</td>
        </tr>
        <tr>
          <td class="text-left">Roland Clarion</td>
          <td class="text-right">Online</td>
          <td class="text-right">Paper Print</td>
          <td class="text-right">2</td>
          <td class="text-right">4.3</td>
          <td class="text-right">129</td>
        </tr>
        <tr>
          <td class="text-left">Hann Samm A. Beleganio</td>
          <td class="text-right">Walkin</td>
          <td class="text-right">T-shirt Print</td>
          <td class="text-right">23</td>
          <td class="text-right">6</td>
          <td class="text-right">337</td>
        </tr>
        <tr>
          <td class="text-left">Cristian Benigay</td>
          <td class="text-right">Online</td>
          <td class="text-right">Photocopy</td>
          <td class="text-right">67</td>
          <td class="text-right">4.3</td>
          <td class="text-right">413</td>
        </tr>
        <tr>
          <td class="text-left">Jay Benigay</td>
          <td class="text-right">Walkin</td>
          <td class="text-right">Load</td>
          <td class="text-right">49</td>
          <td class="text-right">3.9</td>
          <td class="text-right">327</td>
        </tr>
      </tbody>
    </q-markup-table>
  </div>
</template>

<script setup>
import { ref } from "vue";
// import { FontAwesomeIcon } from "@fortawesome/vue-fontawesome";
const option = ref("ambot");

const lightDialog = ref(false);
const darkDialog = ref(false); // Uncomment to enable dark dialog
</script>
