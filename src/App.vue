<template>
  <q-layout view="hHh lpR fFf">
    <q-header  class="bg-orange-6">
      <q-toolbar>
        <q-btn
          flat
          dense
          round
          @click="leftDrawerOpen = !leftDrawerOpen"
          aria-label="Menu"
          icon="menu"
        />

        <q-toolbar-title>
          AWS IP range finder
        </q-toolbar-title>

        <!-- <div>Quasar v{{ $q.version }}</div> -->
      </q-toolbar>
    </q-header>

    <q-drawer
      v-model="leftDrawerOpen"
      show-if-above
      bordered
      content-class="bg-grey-2"
    >
      <q-list>
        <!-- <q-item-label header>AWS IP ranges</q-item-label> -->
        <q-item clickable>
          <q-item-section avatar>
            <q-icon name="school" />
          </q-item-section>
          <router-link to="/" >
            <q-item-section>
              <q-item-label>
                Home
              </q-item-label>
              <q-item-label caption>Home</q-item-label>
            </q-item-section>
          </router-link>
        </q-item>

        <q-item clickable tag="a" target="_blank" href="https://docs.aws.amazon.com/general/latest/gr/aws-ip-ranges.html">
          <q-item-section avatar>
            <q-icon name="code" />
          </q-item-section>
          <q-item-section>
            <q-item-label>Docs</q-item-label>
            <q-item-label caption>AWS Docs</q-item-label>
          </q-item-section>
        </q-item>

        <q-item clickable tag="a" target="_blank" href="https://github.com/prabhatsharma/awsiprangefinder">
          <q-item-section avatar>
            <q-icon name="code" />
          </q-item-section>
          <q-item-section>
            <q-item-label>Github</q-item-label>
            <q-item-label caption>github.com/prabhatsharma/awsiprangefinder</q-item-label>
          </q-item-section>
        </q-item>

      </q-list>
    </q-drawer>

    <q-page-container>
      <router-view></router-view>
    </q-page-container>
  </q-layout>
</template>

<script>
// import RangeFinder from './components/RangeFinder.vue'

export default {
  name: 'LayoutDefault',

  components: {
    // RangeFinder
  },

  data () {
    return {
      leftDrawerOpen: false
    }
  }
}
</script>

<style>
</style>
