<template>
  <div class='row'>
    <HeaderToolBtn :icon='bellIcon' />
    <LangSwitcher />
    <AvatarDropdown v-if='logined' />
  </div>
</template>

<script setup lang='ts'>
import { useLoginedUserStore, useMailboxStore } from 'npool-cli-v2'
import { defineAsyncComponent, computed } from 'vue'

import bellNoMsg from '../../assets/bell-no-msg.svg'
import bellMsg from '../../assets/bell-msg.svg'

const AvatarDropdown = defineAsyncComponent(() => import('src/components/avatar/AvatarDropdown.vue'))
const HeaderToolBtn = defineAsyncComponent(() => import('src/components/header/HeaderToolBtn.vue'))
const LangSwitcher = defineAsyncComponent(() => import('src/components/lang/LangSwitcher.vue'))

const loginedUser = useLoginedUserStore()
const logined = loginedUser.getLogined

const mailbox = useMailboxStore()
const bellIcon = computed(() => mailbox.Notifications.length > 0 ? bellMsg : bellNoMsg)

</script>

<style lang='sass' scoped>
</style>
