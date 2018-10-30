<template>
	<div class="container-fluid">
		<SearchBar @termChange="onTermChange"></SearchBar>
		<div class="row">
			<VideoDetail :video="selectedVideo"></VideoDetail>
			<VideoList :videos="videos" @videoSelect="onVideoSelect"></VideoList>
		</div>
	</div>
</template>

<script>
import axios from 'axios';

import SearchBar from './components/SearchBar';
import VideoList from './components/VideoList';
import VideoDetail from './components/VideoDetail';

const YT = 'AIzaSyDcR8cfDurpI5t1grN7s2zxCm4p239Jv0Y';

export default {
	name: 'App',
	components: {
		SearchBar,
		VideoList,
		VideoDetail,
	},
	data() {
		return {
			videos: [],
			selectedVideo: null,
		};
	},
	methods: {
		async onTermChange(searchTerm) {
			try {
				const { data } = await axios.get('https://www.googleapis.com/youtube/v3/search', {
					params: {
						key: YT,
						type: 'video',
						part: 'snippet',
						q: searchTerm,
					},
				});
				this.videos = data.items;
			} catch (err) {}
		},
		onVideoSelect(video) {
			this.selectedVideo = video;
		},
	},
};
</script>

<style scoped>
</style>
