<script setup lang='ts'>
// ==== Utils ====
import { useResize } from '@/utils/useResize'

// ==== components ====
import Header from './components/Header.vue'
import Left from './components/left/index.vue'
import Right from './components/right/index.vue'
import Center from './components/center/index.vue'

// ==== store ====
import { useScreenStore } from '@/store'

const { screenRef } = useResize()
const store = useScreenStore()
</script>
<template>
	<div :class="['easy-screen-container', store.theme]">
		<div ref="screenRef" class="easy-screen">
			<Header />
			<div class="easy-screen-main">
				<div class="easy-screen-left">
					<Left />
				</div>
				<div class="easy-screen-center">
					<Center />
				</div>
				<div class="easy-screen-right">
					<Right />
				</div>
			</div>
		</div>
	</div>
</template>
<style lang='scss' scoped>
.easy-screen-container {
	--easy-screen-width: 1920px;
  --easy-screen-height: 1080px;
	--es-header-height: 72px;
	--es-block-bg: #222733;
	--easy-screen-bg: rgb(22, 21, 34);
	--easy-screen-text-color: #fff;
	position: relative;
	margin: 0;
	width: 100%;
	height: 100%;
	background-size: 100% 100%;
	overflow: hidden;
	background: var(--easy-screen-bg);
	color: var(--easy-screen-text-color);
}
.easy-screen {
  position: absolute;
  user-select: none;
  top: 50%;
  left: 50%;
  width: var(--easy-screen-width);
  height: var(--easy-screen-height);
  margin-left: calc(var(--easy-screen-width) * 0.5 - var(--easy-screen-width));
  margin-top: calc(var(--easy-screen-height) * 0.5 - var(--easy-screen-height));
  background-size: 100% 100%;
	padding: 0 20px;
	&-main {
		position: relative;
		display: flex;
		height: calc(100% - var(--es-header-height));
	}
	&-center {
		flex: 1;
		width: calc(var(--easy-screen-width) - 1000px);
	}
	&-left, &-right {
		width: 460px;
	}
}
.light {
	--easy-screen-bg: rgb(238, 238, 238);
	--es-block-bg: #fff;
	--easy-screen-text-color: rgb(22, 21, 34);
}
</style>
