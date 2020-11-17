<template>
  <q-layout view="lHh Lpr lFf">
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
          List Application
        </q-toolbar-title>

        <div>Running on: Quasar v{{ $q.version }} | Laravel v7.29</div>
      </q-toolbar>
    </q-header>

    <q-drawer
      v-model="leftDrawerOpen"
      show-if-not-above
      bordered
      content-class="bg-grey-3"
    >
      <q-list>
        <q-item-label
          header
          class="text-grey-8"
        >
          Useful Links
        </q-item-label>
        <EssentialLink
          v-for="link in essentialLinks"
          :key="link.title"
          v-bind="link"
        />
      </q-list>
    </q-drawer>

    <q-page-container>
      <router-view />
    </q-page-container>
  </q-layout>
</template>

<script>
import EssentialLink from 'components/EssentialLink.vue'

const linksData = [
  {
    title: 'Site repo',
    caption: 'github.com/connf/list',
    icon: 'code',
    link: 'https://github.com/connf/list'
  },
  {
    title: 'API repo',
    caption: 'github.com/connf/api.list',
    icon: 'code',
    link: 'https://github.com/connf/api.list'
  },
  {
    title: 'LinkedIn',
    caption: '/connah-fearnley-4000a166',
    icon: 'public',
    link: 'https://www.linkedin.com/in/connah-fearnley-4000a166/'
  }
];

export default {
  name: 'MainLayout',
  components: { EssentialLink },
  data () {
    return {
      leftDrawerOpen: true,
      essentialLinks: linksData
    }
  }
}
</script>
