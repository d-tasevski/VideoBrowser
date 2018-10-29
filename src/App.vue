<template>
	<div>
		<SearchBar @termChange="onTermChange"></SearchBar>
		<p>Hi there!!!</p>
		<VideoList :videos="videos"></VideoList>
	</div>
</template>

<script>
import axios from 'axios';

import SearchBar from './components/SearchBar';
import VideoList from './components/VideoList';

const YT = 'AIzaSyDcR8cfDurpI5t1grN7s2zxCm4p239Jv0Y';

export default {
	name: 'App',
	components: {
		SearchBar,
		VideoList,
	},
	data() {
		return {
			videos: [],
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
			} catch (err) {
				// console.error(err);
			}
		},
	},
};
</script>

<style>
</style>
