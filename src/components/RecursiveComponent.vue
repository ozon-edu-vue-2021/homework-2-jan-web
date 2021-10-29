<template>
	<div>
		<ul v-if="item.contents && item.contents.length > 0">
			<div class="folder" @click="changeVisability">
				<icon-closed-folder v-if="isClosed" />
				<icon-opened-folder v-if="!isClosed" />
				<h3 class="dir-name">
					{{ item.name }}
				</h3>
			</div>
			<div v-if="isVisible">
				<recursive-component
					v-for="(child, subIndex) in item.contents"
					:item="child"
					:key="subIndex"
					:isFileSelected="isFileSelected"
					@file="fileSelected"
				/>
			</div>
		</ul>
		<li v-if="item.type === 'file'" :class="fileClasses" @click="selected(item.name)">
			{{ item.name }}
		</li>
		<li v-if="item.type === 'link'" :class="linkClasses" @click="selected(item.name)">
			{{ item.name }}
		</li>
	</div>
</template>
<script>
import IconClosedFolder from "./Icons/IconClosedFolder";
import IconOpenedFolder from "./Icons/IconOpenedFolder";
export default {
	name: "RecursiveComponent",
	props: {
		item: {
			type: [Object, String],
			required: true,
		},
		isFileSelected: {
			type: Boolean

		}
	},
	data: () => ({
		isVisible: false,
		isClosed: true,
		isSelected: false,
		canItSelects: true

	}),
	computed: {
		fileClasses() {
			return ['file-name', { 'selected': this.isSelected}];
		},
		linkClasses() {
			return ['link-name', { 'selected': this.isSelected}];
		},

	},
	methods: {
		changeVisability() {
			this.isVisible = !this.isVisible;
			this.isClosed = !this.isClosed;
		},
		selected(name) {
			this.isSelected = !this.isSelected;
			this.$emit('file', name);

		},
		fileSelected() {
			this.isSelected = false;
    }
	},
	components: {
		IconClosedFolder,
		IconOpenedFolder,
	},
};
</script>
<style scoped>
.dir-name {
	color: tomato;
	margin-left: 10px;
}
.file-name {
	color: brown;
}
.link-name {
	color: blue;
}
.selected {
	color: green;
}
.folder {
	display: inline-flex;
	align-items: center;
}
</style>
