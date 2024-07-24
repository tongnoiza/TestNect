<template>
	
	<!-- Main Sidebar -->
	<a-layout-sider
		collapsible
		class="sider-primary"
		breakpoint="lg"
		collapsed-width="0"
		width="250px"
		:collapsed="sidebarCollapsed"
		@collapse="$emit('toggleSidebar', ! sidebarCollapsed)"
		:trigger="null"
		:class="['ant-layout-sider-' + sidebarColor, 'ant-layout-sider-' + sidebarTheme]"
		theme="light"
		:style="{ backgroundColor: 'transparent',}">
		
			<div class="brand">
				<img style="height: 156px;border-radius: 76px;" src="user.jpg"/>
				<br>
				<span style="margin-top: 5px;">นพ. ทดสอบ ระบบแพทย์</span></div>
			<hr>

			<!-- Sidebar Navigation Menu -->
			<a-menu theme="light" mode="inline">
				<a-menu-item>
					<router-link to="/tables">
					
						<span class="label">หน้าหลัก</span>
					</router-link>
				</a-menu-item>
				<a-menu-item>
					<router-link to="/dashboard">
						
						<span class="label">ขึ้นทะเบียนสำเร็จ</span>
					</router-link>
				</a-menu-item>
				<a-menu-item>
					<router-link to="/billing">
						<span class="label">User Management</span>
					</router-link>
				</a-menu-item>
			</a-menu>
	</a-layout-sider>

</template>

<script>

	export default ({
		props: {
			// Sidebar collapsed status.
			sidebarCollapsed: {
				type: Boolean,
				default: false,
			},
			
			// Main sidebar color.
			sidebarColor: {
				type: String,
				default: "primary",
			},
			
			// Main sidebar theme : light, white, dark.
			sidebarTheme: {
				type: String,
				default: "light",
			},
		},
		data() {
			return {
				// sidebarCollapsedModel: this.sidebarCollapsed,
			}
		},
	})

</script>
