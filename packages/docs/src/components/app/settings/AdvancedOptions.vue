<template>
  <div class="mb-3">
    <v-label :text="t('communication')" class="mb-2 font-weight-medium" />

    <v-messages :messages="t('communication-message')" active />
  </div>

  <banner-option />

  <notifications-option />

  <div class="d-flex justify-end">
    <v-btn
      :text="t('reset-all')"
      color="error"
      size="small"
      variant="flat"
      @click="onResetAll"
    />
  </div>

  <v-divider class="my-3" />

  <developer-mode />
</template>

<script setup>
  // Components
  import BannerOption from './options/BannerOption.vue'
  import DeveloperMode from './DeveloperMode.vue'
  import NotificationsOption from './options/NotificationsOption.vue'

  // Composables
  import { useI18n } from 'vue-i18n'

  // Stores
  import { useUserStore } from '@/store/user'

  const { t } = useI18n()
  const user = useUserStore()

  function onResetAll () {
    user.banner = true
    user.notifications.read = []
    user.notifications.show = true
    user.notifications.last.banner = []
    user.quickbar = true
  }
</script>
