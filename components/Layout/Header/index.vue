<template>
  <div>
    <a-row class="header">
      <a-col :span="20" class="header-menu">
        <nuxt-link to="/">
          <a-icon type="weibo" class="icon_menu" />
        </nuxt-link>
        TodoApp
      </a-col>
      <a-col :span="4">
        <div class="user" v-if="isLogin">
          <a-dropdown>
            <a-menu slot="overlay" @click="handleMenuClick" class="menu-item">
              <a-menu-item> <nuxt-link to="/">Logout</nuxt-link> </a-menu-item>
              <a-menu-item> Info User </a-menu-item>
            </a-menu>
            <a-badge :count="1"
              ><a-avatar shape="square" icon="user"
            /></a-badge>
          </a-dropdown>
        </div>
        <div class="user" v-else>
          <a-button ghost @click="login">
            <nuxt-link to="/"> Login </nuxt-link>
          </a-button>
        </div>
      </a-col>
    </a-row>
  </div>
</template>

<script>
export default {
  name: 'Header',
  data() {
    return {
      isLogin: null,
    }
  },
  created() {
    if (typeof window !== 'undefined') {
      const data = localStorage.getItem('token')
      if (data) {
        this.isLogin = data
      } else {
        this.isLogin = null
      }
    }
  },
  methods: {
    login() {
      localStorage.setItem('token', 1223)
    },
    handleMenuClick(e) {
      if(e.key == 'item_0'){
          localStorage.removeItem('token')
          
      }
    },
  },
}
</script>

<style>
.header {
  background: #333;
  height: 64px;
}
.header .header-menu {
  color: #fff;
  font-size: 30px;
  font-weight: normal;
}
.icon_menu {
  font-size: 32px;
  line-height: 64px;
  margin: 0 20px;
}
.user {
  line-height: 64px;
}
.menu-item{
    margin-top: 5px;
}
</style>
