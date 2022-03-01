<template>
  <div>
    <Header />
    <div class="menu-content">
        <Menu />
        <Content />
    </div>
  </div>
</template>

<script>
import Header from '../components/Layout/Header'
import Menu from './Layout/Menu/index.vue'
import Content from './Layout/Content/index.vue'
export default {
  name: 'Container',
  components: { Header, Menu, Content },
}
</script>

<style>
.menu-content{
    display: flex;
    width: 100%;
}
</style>
