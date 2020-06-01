<template>
  <div class="user-wrapper">
    <div>
      <a-menu class="usermenu-display-inline" mode="horizontal" style="display:none;">
        <a-menu-item key="mail1"> <a-icon type="mail" />基础信息</a-menu-item>
        <a-menu-item key="mail2"> <a-icon type="mail" />基础信息</a-menu-item>
        <a-menu-item key="mail3"> <a-icon type="mail" />基础信息</a-menu-item>
        <a-menu-item key="mail4"> <a-icon type="mail" />基础信息</a-menu-item>
        <a-menu-item key="mail5"> <a-icon type="mail" />基础信息</a-menu-item>
        <a-menu-item key="mail6"> <a-icon type="mail" />基础信息</a-menu-item>
        <a-menu-item key="app"> <a-icon type="appstore" />应收管理</a-menu-item>
      </a-menu>
    </div>
    <div class="content-box">
      <notice-icon class="action" />
      <a-dropdown>
        <span class="action ant-dropdown-link user-dropdown-menu">
          <a-avatar
            class="avatar"
            size="small"
            :src="avatar"
          />
          <span>{{ nickname }}</span>
        </span>
        <a-menu
          slot="overlay"
          class="user-dropdown-menu-wrapper"
        >
          <a-menu-item key="0">
            <router-link :to="{ name: 'center' }">
              <a-icon type="user" />
              <span>个人中心</span>
            </router-link>
          </a-menu-item>
          <a-menu-item key="1">
            <router-link :to="{ name: 'settings' }">
              <a-icon type="setting" />
              <span>账户设置</span>
            </router-link>
          </a-menu-item>
          <a-menu-item
            key="2"
            disabled
          >
            <a-icon type="setting" />
            <span>测试</span>
          </a-menu-item>
          <a-menu-divider />
          <a-menu-item key="3">
            <a
              href="javascript:;"
              @click="handleLogout"
            >
              <a-icon type="logout" />
              <span>退出登录</span>
            </a>
          </a-menu-item>
        </a-menu>
      </a-dropdown>
    </div>
  </div>
</template>

<script>
import NoticeIcon from '@/components/NoticeIcon';
import { mapActions, mapGetters } from 'vuex';

export default {
	name: 'UserMenu',
	components: {
		NoticeIcon
	},
	computed: {
		...mapGetters(['nickname', 'avatar'])
	},
	methods: {
		...mapActions(['Logout']),
		handleLogout () {
			this.$confirm({
				title: '提示',
				content: '真的要注销登录吗 ?',
				onOk: () => {
					return this.Logout({})
						.then(() => {
							setTimeout(() => {
								window.location.reload();
							}, 16);
						})
						.catch(err => {
							this.$message.error({
								title: '错误',
								description: err.message
							});
						});
				},
				onCancel () {}
			});
		}
	}
};
</script>
<style scoped>
  .usermenu-display-inline {
    display: inline-block;
  }
</style>
