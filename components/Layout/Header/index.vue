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
          <span style="margin-right: 24px">
            <a-badge :count="1"
              ><a-avatar shape="square" icon="user"
            /></a-badge>
          </span>
        </div>
        <div class="user" v-else>
          <a-button ghost>
              <nuxt-link to="/login">
                  Login
              </nuxt-link>
          </a-button>
        </div>
      </a-col>
    </a-row>
  </div>
</template>

<script>
export default {
    name: 'Header',
    data () {
        return {
            isLogin : false
        }
    }
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
.user{
    line-height: 64px;
}
</style>
