<template>
  <div :style="collapsed ? 'width: 80px' : 'width: 256px'" >
    <a-button type="primary" @click="toggleCollapsed" :style="collapsed ? 'width: 80px' : 'width: 256px'">
      <a-icon :type="collapsed ? 'menu' : 'menu'" />
    </a-button>
    <a-menu
      :inline-collapsed="collapsed"
      theme="dark"
      mode="inline"
      :default-selected-keys="['1']"
    >
      <a-menu-item key="1">
        <a-icon type="solution" />
        <span>Home</span>
      </a-menu-item>
      <a-menu-item key="2">
        <a-icon type="table" />
        <span>Todo</span>
      </a-menu-item>
    </a-menu>
  </div>
</template>

<script>
export default {
  name: 'Menu',
  data() {
    return {
      collapsed: false,
    }
  },
  methods: {
    toggleCollapsed() {
      this.collapsed = !this.collapsed
    },
  },
}
</script>

<style></style>
