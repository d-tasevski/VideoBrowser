<template>
	<div>
		<ul>Video List</ul>
		<VideoListItem v-for="video in videos" :key="video.etag" :video="video"></VideoListItem>
	</div>
</template>

<script>
import VideoListItem from './VideoListItem';

export default {
	name: 'VideoList',
	props: {
		videos: Array,
	},
	components: {
		VideoListItem,
	},
};
</script>

<style>
</style>
