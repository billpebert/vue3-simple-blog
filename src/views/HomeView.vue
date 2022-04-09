<template>
	<div class="home">
		<!-- Part 1 -->
		<!-- <h1>Home</h1>
		<h2>Refs</h2>
		<p>{{ ninjaOne.name }} - {{ ninjaOne.age }}</p>
		<button @click="updateNinjaOne">Update ninja one</button>

		<h2>Reactive</h2>
		<p>{{ ninjaTwo.name }} - {{ ninjaTwo.age }}</p>
		<button @click="updateNinjaTwo">Update ninja two</button> -->

		<!-- Part 2 -->
		<h1>Home</h1>

		<div v-if="error">
			{{ error }}
		</div>

		<div v-if="posts.length">
			<PostList :posts="posts" />
			<!-- <PostList v-if="showPosts" :posts="posts" /> -->
		</div>
		<div v-else>Loading...</div>

		<!-- <button @click="showPosts = !showPosts">toggle posts</button>
		<button @click="posts.pop()">Delete a post</button> -->
	</div>
</template>

<script>
// @ is an alias to /src
import PostList from "../components/PostList.vue";
import getPosts from "../composable/getPosts";
export default {
	name: "HomeView",
	components: {
		PostList,
	},
	setup() {
		//PART 1
		// const ninjaOne = ref({ name: "billy", age: 28 });
		// const ninjaTwo = reactive({ name: "veronica", age: 35 });

		// const updateNinjaOne = () => {
		// 	ninjaOne.value.age = 40;
		// };

		// const updateNinjaTwo = () => {
		// 	ninjaTwo.age = 43;
		// };

		// return { ninjaOne, updateNinjaOne, ninjaTwo, updateNinjaTwo };

		// PART 2
		// destructure the value from getPosts
		const { posts, error, load } = getPosts();

		load();

		// const showPosts = ref(true);

		return { posts, error };
	},
};
</script>
