<template>
<section>
	<component :is="'h' + h" :class="h < 5 ? $style['h' + h] : null">{{ block.title }}</component>

	<div class="_gaps">
		<XBlock v-for="child in block.children" :key="child.id" :page="page" :block="child" :h="h + 1"/>
	</div>
</section>
</template>

<script lang="ts" setup>
import { defineAsyncComponent } from 'vue';
import * as Misskey from 'misskey-js';
import { SectionBlock } from './block.type';

const XBlock = defineAsyncComponent(() => import('./page.block.vue'));

defineProps<{
	block: SectionBlock,
	h: number,
	page: Misskey.entities.Page,
}>();
</script>

<style lang="scss" module>
.h2 {
	font-size: 1.35em;
	margin: 0 0 0.5em 0;
}

.h3 {
	font-size: 1em;
	margin: 0 0 0.5em 0;
}

.h4 {
	font-size: 1em;
	margin: 0 0 0.5em 0;
}
</style>
