<template>
  <q-layout view="hHh Lpr lFf">
    <q-header elevated>
      <q-toolbar>
        <q-btn
          flat
          dense
          round
          icon="menu"
          aria-label="Menu"
          @click="leftDrawerOpen = !leftDrawerOpen"
        />
        <q-toolbar-title>
          WhatsGood
        </q-toolbar-title>
      </q-toolbar>
    </q-header>

    <q-drawer
      v-model="leftDrawerOpen"
      show-if-above
      bordered
      content-class="bg-grey-1"
    >
      <q-scroll-area class="fit">
        <q-list v-for="(menuItem, index) in menuList" :key="index">
          <q-item clickable :active="menuItem.label === 'Outbox'" v-ripple>
            <q-item-section avatar>
              <q-icon :name="menuItem.icon" />
            </q-item-section>

            <q-item-section>
              {{ menuItem.label }}
            </q-item-section>
          </q-item>

          <q-separator v-if="menuItem.separator" />
        </q-list>
      </q-scroll-area>
    </q-drawer>

    <q-page-container>
      <router-view />
    </q-page-container>
  </q-layout>
</template>

<script>
export default {
  name: "MainLayout",

  data() {
    return {
      leftDrawerOpen: false,
      menuList: [
        {
          icon: "inbox",
          label: "Inbox",
          separator: true
        },
        {
          icon: "send",
          label: "Outbox",
          separator: false
        },
        {
          icon: "delete",
          label: "Trash",
          separator: false
        },
        {
          icon: "error",
          label: "Spam",
          separator: true
        },
        {
          icon: "settings",
          label: "Settings",
          separator: false
        },
        {
          icon: "feedback",
          label: "Send Feedback",
          separator: false
        },
        {
          icon: "help",
          iconColor: "primary",
          label: "Help",
          separator: false
        }
      ]
    };
  }
};
</script>
