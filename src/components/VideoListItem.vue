<template>
	<li class="list-group-item media video-list-item" @click="onVideoSelect">
		<img class="mr-3" :src="thumbnailURL" alt="Video thumbnail">
		<div class="media-body">{{ video.snippet.title }}</div>
	</li>
</template>

<script>
export default {
	name: 'VideoListItem',
	props: {
		video: Object,
	},
	computed: {
		thumbnailURL() {
			return this.video.snippet.thumbnails.default.url;
		},
	},
	methods: {
		onVideoSelect() {
			this.$emit('videoSelect', this.video);
		},
	},
};
</script>

<style scoped>
.video-list-item {
	display: flex;
	font-size: 80%;
}

.video-list-item:hover {
	background-color: #eee;
}
</style>
