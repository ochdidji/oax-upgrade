<template lang="pug">
  v-app(v-hotkey="keymap" , :class="classes", :dark="VIEW_DARK")
    v-navigation-drawer.pb-0(app fixed left disable-resize-watcher disable-route-watcher v-model="menu", :class="classesLeft", :width="$panelLeft", style="overflow: hidden")
      router-view(name="panel")
    v-navigation-drawer.pb-0(app fixed right disable-resize-watcher disable-route-watcher v-model="drawer", :class="classesRight", :width="$panel", style="overflow: hidden")
      div(style="height: 100%; overflow: auto")
        app-detail(v-if="SPEC_OPERATION", :operation="SPEC_OPERATION")
    app-toolbar
    v-content#main
      router-view
    app-log-dialog(v-model="log")
    app-tour(v-if="UI_HIGHLIGHT")
    appFab
    v-snackbar(:value="!!serviceWorker.registration" top :timeout="1e10") Update ready
      a.snackbar-action(@click="reload") Reload
    #cm-full
</template>

<script>
export { default } from './AppScript'
</script>

<style lang="stylus">
  @import '../style/index.styl'
</style>
