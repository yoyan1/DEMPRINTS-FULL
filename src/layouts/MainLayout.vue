<template>
  <q-layout view="lHh Lpr lFf">
    <q-header elevated style="background-color: dirty-white">
      <q-toolbar>
        <q-btn
          flat
          dense
          round
          icon="menu"
          aria-label="Menu"
          @click="toggleLeftDrawer"
        />

        <q-toolbar-title>
          <q-img
            src="/LogoV3.jpg"
            style="height: 45px; width: 45px"
            class="rounded-full"
          />
        </q-toolbar-title>

        <!-- <div>Quasar v{{ $q.version }}</div> -->
      </q-toolbar>
    </q-header>

    <q-drawer v-model="leftDrawerOpen" show-if-above bordered>
      <q-list>
        <q-item-label header>
          <q-img
            src="/profile.png"
            style="height: 45px; width: 45px"
            class="rounded-full mr-2"
          />
          <q-span class="fs-1">Cristian Benigay</q-span>
        </q-item-label>

        <EssentialLink
          v-for="link in linksList"
          :key="link.title"
          v-bind="link"
        />

        <!-- Corrected dropdown -->
        <q-btn-dropdown flat label="More Options">
          <q-list>
            <!-- <q-item clickable v-close-popup @click="onItemClick">
              <q-item-section>
                <q-item-label>Photos</q-item-label>
              </q-item-section>
            </q-item> -->
            <q-item clickable v-close-popup @click="onItemClick">
              <q-item-section>
                <q-item-label>Settings</q-item-label>
              </q-item-section>
            </q-item>
          </q-list>
        </q-btn-dropdown>

      </q-list>
    </q-drawer>

    <q-page-container>
      <router-view />
    </q-page-container>
  </q-layout>
</template>

<script setup>
import { ref } from "vue";
import EssentialLink from "components/EssentialLink.vue";

defineOptions({
  name: "MainLayout",
});

const linksList = [
  {
    title: "Dashboard",
    icon: "school",
    link: "/",
  },
  {
    title: "Transaction",
    icon: "code",
    link: "#/transaction",
  },
  // {
  //   title: "Sales Module",
  //   icon: "chat",
  //   link: "",
  // },
];

const leftDrawerOpen = ref(false);

function toggleLeftDrawer() {
  leftDrawerOpen.value = !leftDrawerOpen.value;
}

function onItemClick() {
  console.log("Item clicked!");
}
</script>
