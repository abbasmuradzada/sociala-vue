<template>
	<div class="row">
		<div class="col-lg-12">
			<div class="card w-100 border-0 p-0 bg-white shadow-xss rounded-xxl">
				<div class="card-body h250 p-0 rounded-xxl overflow-hidden m-3">
					<img :src="myUser.backgroundPicture" alt="image" />
				</div>
				<div class="card-body p-0 position-relative">
					<figure
						class="avatar position-absolute w100 z-index-1"
						style="top: -40px; left: 30px"
					>
						<img
							:src="myUser.profilePicture"
							alt="image"
							class="float-right p-1 bg-white rounded-circle w-100"
						/>
					</figure>
					<h4 class="fw-700 font-sm mt-2 mb-lg-5 mb-4 pl-15">
						{{ myUser.userName }}
						<span class="fw-500 font-xssss text-grey-500 mt-1 mb-3 d-block">
							{{ myUser.email }}
						</span>
					</h4>
					<!-- <div
						class="
              d-flex
              align-items-center
              justify-content-center
              position-absolute-md
              right-15
              top-0
              me-2
            "
					>
						<a
							@click="sendOrRemoveSubscribe(myUser._id)"
							v-if="userId !== this.$route.params.id"
							class="
                d-none
                cursor-pointer
                d-lg-block
                bg-success
                p-3
                z-index-1
                rounded-3
                text-white
                font-xsssss
                text-uppercase
                fw-700
                ls-3
              "
							>{{ followStatus }}</a
						>
						<a
							href="#"
							class="
                d-none d-lg-block
                bg-greylight
                btn-round-lg
                ms-2
                rounded-3
                text-grey-700
              "
							><i class="feather-mail font-md"></i
						></a>
						<a
							href="#"
							id="dropdownMenu4"
							class="
                d-none d-lg-block
                bg-greylight
                btn-round-lg
                ms-2
                rounded-3
                text-grey-700
              "
							data-toggle="dropdown"
							aria-haspopup="true"
							aria-expanded="false"
							><i class="ti-more font-md tetx-dark"></i
						></a>
						<div
							class="
                dropdown-menu dropdown-menu-end
                p-4
                rounded-xxl
                border-0
                shadow-lg
              "
							aria-labelledby="dropdownMenu4"
						>
							<div class="card-body p-0 d-flex">
								<i class="feather-bookmark text-grey-500 me-3 font-lg"></i>
								<h4 class="fw-600 text-grey-900 font-xssss mt-0 me-0">
									Save Link
									<span
										class="d-block font-xsssss fw-500 mt-1 lh-3 text-grey-500"
										>Add this to your saved items</span
									>
								</h4>
							</div>
							<div class="card-body p-0 d-flex mt-2">
								<i class="feather-alert-circle text-grey-500 me-3 font-lg"></i>
								<h4 class="fw-600 text-grey-900 font-xssss mt-0 me-0">
									Hide Post
									<span
										class="d-block font-xsssss fw-500 mt-1 lh-3 text-grey-500"
										>Save to your saved items</span
									>
								</h4>
							</div>
							<div class="card-body p-0 d-flex mt-2">
								<i class="feather-alert-octagon text-grey-500 me-3 font-lg"></i>
								<h4 class="fw-600 text-grey-900 font-xssss mt-0 me-0">
									Hide all from Group
									<span
										class="d-block font-xsssss fw-500 mt-1 lh-3 text-grey-500"
										>Save to your saved items</span
									>
								</h4>
							</div>
							<div class="card-body p-0 d-flex mt-2">
								<i class="feather-lock text-grey-500 me-3 font-lg"></i>
								<h4 class="fw-600 mb-0 text-grey-900 font-xssss mt-0 me-0">
									Unfollow Group
									<span
										class="d-block font-xsssss fw-500 mt-1 lh-3 text-grey-500"
										>Save to your saved items</span
									>
								</h4>
							</div>
						</div>
					</div> -->
				</div>

				<div class="card-body d-block w-100 shadow-none mb-0 p-0 border-top-xs">
					<ul
						class="
              nav nav-tabs
              h55
              d-flex
              product-info-tab
              border-bottom-0
              ps-4
            "
						id="pills-tab"
						role="tablist"
					>
						<li class="active list-inline-item me-5">
							<a
								class="
                  fw-700
                  font-xssss
                  text-grey-500
                  pt-3
                  pb-3
                  ls-1
                  d-inline-block
                  active
                "
								href="#navtabs1"
								data-toggle="tab"
								>About</a
							>
						</li>
						<li class="list-inline-item me-5">
							<a
								class="
                  fw-700
                  font-xssss
                  text-grey-500
                  pt-3
                  pb-3
                  ls-1
                  d-inline-block
                "
								href="#navtabs4"
								data-toggle="tab"
								>Video</a
							>
						</li>
						<li class="list-inline-item me-5">
							<a
								class="
                  fw-700
                  me-sm-5
                  font-xssss
                  text-grey-500
                  pt-3
                  pb-3
                  ls-1
                  d-inline-block
                "
								href="#navtabs7"
								data-toggle="tab"
								>Media</a
							>
						</li>
					</ul>
				</div>
			</div>
		</div>
		<div class="col-xl-4 col-xxl-3 col-lg-4 pe-0">
			<router-link
				:to="{ name: 'FollowerList', params: { userName, } }"
			>
				<div
					class="
            cursor-pointer
            card
            w-100
            shadow-xss
            rounded-xxl
            border-0
            mb-3
            mt-3
          "
				>
					<div class="card-body border-0">
						<div class="row">
							<h4
								class="profile-statictic-text font-xsss d-flex align-items-sm-center ml-3 fw-700"
							>
								<a class="text-center menu-icon chat-active-btn"
									><i
										class="profile-statictic-icon feather-users font-md text-black"
									></i
								></a>
								<span class="mb-1">{{ myUser.followersCount }} Follower</span>
							</h4>
						</div>
					</div>
				</div>
			</router-link>

			<router-link :to="{ name: 'FollowList', params: { userName, } }">
				<div
					class="
            cursor-pointer
            card
            w-100
            shadow-xss
            rounded-xxl
            border-0
            mb-3
            mt-3
          "
				>
					<div class="card-body border-0">
						<div class="row">
							<h4
								class="profile-statictic-text font-xsss d-flex align-items-sm-center ml-3 fw-700"
							>
								<a class="text-center menu-icon chat-active-btn"
									><i
										class="profile-statictic-icon feather-user-check font-md text-black"
									></i
								></a>
								<span class="mb-1">{{ myUser.followsCount }} Follow</span>
							</h4>
						</div>
					</div>
				</div>
			</router-link>
			<div
				class="
          cursor-pointer
          card
          w-100
          shadow-xss
          rounded-xxl
          border-0
          mb-3
          mt-3
        "
			>
				<div class="card-body border-0">
					<div class="row">
						<h4
							class=" profile-statictic-text font-xsss d-flex align-items-sm-center ml-3 fw-700"
						>
							<a class="text-center menu-icon chat-active-btn"
								><i
									class="profile-statictic-icon feather-list font-md text-black"
								></i
							></a>
							<span class="mb-1">{{ myUser.postsCount }} Post</span>
						</h4>
					</div>
				</div>
			</div>
			<div class="card w-100 shadow-xss rounded-xxl border-0 mb-3">
				<div class="card-body d-block p-4">
					<h4 class="fw-700 mb-3 font-xsss text-grey-900">About</h4>
					<p class="fw-500 text-grey-500 lh-24 font-xssss mb-0">
						Lorem ipsum dolor sit amet, consectetur adipiscing elit. Morbi nulla
						dolor, ornare at commodo non, feugiat non nisi. Phasellus faucibus
						mollis pharetra. Proin blandit ac massa sed rhoncus
					</p>
				</div>
				<div class="card-body border-top-xs d-flex">
					<i class="feather-lock text-grey-500 me-3 font-lg"></i>
					<h4 class="fw-700 text-grey-900 font-xssss mt-0">
						Private
						<span class="d-block font-xssss fw-500 mt-1 lh-3 text-grey-500"
							>What's up, how are you?</span
						>
					</h4>
				</div>

				<div class="card-body d-flex pt-0">
					<i class="feather-eye text-grey-500 me-3 font-lg"></i>
					<h4 class="fw-700 text-grey-900 font-xssss mt-0">
						Visble
						<span class="d-block font-xssss fw-500 mt-1 lh-3 text-grey-500"
							>Anyone can find you</span
						>
					</h4>
				</div>
				<div class="card-body d-flex pt-0">
					<i class="feather-map-pin text-grey-500 me-3 font-lg"></i>
					<h4 class="fw-700 text-grey-900 font-xssss mt-1">Flodia, Austia</h4>
				</div>
				<div class="card-body d-flex pt-0">
					<i class="feather-users text-grey-500 me-3 font-lg"></i>
					<h4 class="fw-700 text-grey-900 font-xssss mt-1">Genarel Group</h4>
				</div>
			</div>
			<div class="card w-100 shadow-xss rounded-xxl border-0 mb-3">
				<div class="card-body d-flex align-items-center p-4">
					<h4 class="fw-700 mb-0 font-xssss text-grey-900">Photos</h4>
					<a href="#" class="fw-600 ms-auto font-xssss text-primary">See all</a>
				</div>
				<div class="card-body d-block pt-0 pb-2">
					<div class="row">
						<div class="col-6 mb-2 pe-1">
							<a href="../assets/images/e-2.jpg" data-lightbox="roadtrip"
								><img
									src="../assets/images/e-2.jpg"
									alt="image"
									class="img-fluid rounded-3 w-100"
							/></a>
						</div>
						<div class="col-6 mb-2 ps-1">
							<a href="../assets/images/e-3.jpg" data-lightbox="roadtrip"
								><img
									src="../assets/images/e-3.jpg"
									alt="image"
									class="img-fluid rounded-3 w-100"
							/></a>
						</div>
						<div class="col-6 mb-2 pe-1">
							<a href="../assets/images/e-4.jpg" data-lightbox="roadtrip"
								><img
									src="../assets/images/e-4.jpg"
									alt="image"
									class="img-fluid rounded-3 w-100"
							/></a>
						</div>
						<div class="col-6 mb-2 ps-1">
							<a href="../assets/images/e-5.jpg" data-lightbox="roadtrip"
								><img
									src="../assets/images/e-5.jpg"
									alt="image"
									class="img-fluid rounded-3 w-100"
							/></a>
						</div>
						<div class="col-6 mb-2 pe-1">
							<a href="../assets/images/e-2.jpg" data-lightbox="roadtrip"
								><img
									src="../assets/images/e-2.jpg"
									alt="image"
									class="img-fluid rounded-3 w-100"
							/></a>
						</div>
						<div class="col-6 mb-2 ps-1">
							<a href="../assets/images/e-1.jpg" data-lightbox="roadtrip"
								><img
									src="../assets/images/e-1.jpg"
									alt="image"
									class="img-fluid rounded-3 w-100"
							/></a>
						</div>
					</div>
				</div>
				<div class="card-body d-block w-100 pt-0">
					<a
						href="#"
						class="
              p-2
              lh-28
              w-100
              d-block
              bg-grey
              text-grey-800 text-center
              font-xssss
              fw-700
              rounded-xl
            "
						><i class="feather-external-link font-xss me-2"></i> More</a
					>
				</div>
			</div>
		</div>
		<div class="col-xl-8 col-xxl-9 col-lg-8">
			<div
				class="
          card
          w-100
          shadow-xss
          rounded-xxl
          border-0
          ps-4
          pt-4
          pe-4
          pb-3
          mb-3
          mt-3
        "
			>
				<div class="card-body p-0">
					<span
						@click="createPost"
						class="
              font-xssss
              fw-600
              text-grey-500
              card-body
              p-0
              d-flex
              align-items-center
              cursor-pointer
            "
						><i
							class="
                btn-round-sm
                font-xs
                text-primary
                feather-edit-3
                me-2
                bg-greylight
              "
						></i
						>Create Post</span
					>
				</div>
				<div class="card-body p-0 mt-3 position-relative">
					<figure class="avatar position-absolute ms-2 mt-1 top-5">
						<img
							:src="myUser.profilePicture"
							alt="image"
							class="shadow-sm rounded-circle w30"
						/>
					</figure>
					<textarea
						v-model="data.content"
						name="message"
						class="
              h100
              bor-0
              w-100
              rounded-xxl
              p-2
              ps-5
              font-xssss
              text-grey-500
              fw-500
              border-light-md
              theme-dark-bg
            "
						cols="30"
						rows="10"
						placeholder="What's on your mind?"
					></textarea>
				</div>
				<div class="card-body d-flex p-0 mt-0 align-items-center">
					<i class="font-md text-success feather-image me-2"></i>
					<v-file-input
						:style="{
							margin: '0 20px 0 0',
						}"
						@change="changeType"
						v-model="data.uploadObject"
						placeholder="Photo / Video"
						prepend-icon=""
						type="file"
					>
					</v-file-input>
					<a
						href="#"
						class="ms-auto"
						id="dropdownMenu8"
						data-toggle="dropdown"
						aria-haspopup="true"
						aria-expanded="false"
						><i
							class="
                ti-more-alt
                text-grey-900
                btn-round-md
                bg-greylight
                font-xss
              "
						></i
					></a>
					<div
						class="
              dropdown-menu dropdown-menu-end
              p-4
              rounded-xxl
              border-0
              shadow-lg
            "
						aria-labelledby="dropdownMenu8"
					>
						<div class="card-body p-0 d-flex">
							<i class="feather-bookmark text-grey-500 me-3 font-lg"></i>
							<h4 class="fw-600 text-grey-900 font-xssss mt-0 me-4">
								Save Link
								<span class="d-block font-xsssss fw-500 mt-1 lh-3 text-grey-500"
									>Add this to your saved items</span
								>
							</h4>
						</div>
						<div class="card-body p-0 d-flex mt-2">
							<i class="feather-alert-circle text-grey-500 me-3 font-lg"></i>
							<h4 class="fw-600 text-grey-900 font-xssss mt-0 me-4">
								Hide Post
								<span class="d-block font-xsssss fw-500 mt-1 lh-3 text-grey-500"
									>Save to your saved items</span
								>
							</h4>
						</div>
						<div class="card-body p-0 d-flex mt-2">
							<i class="feather-alert-octagon text-grey-500 me-3 font-lg"></i>
							<h4 class="fw-600 text-grey-900 font-xssss mt-0 me-4">
								Hide all from Group
								<span class="d-block font-xsssss fw-500 mt-1 lh-3 text-grey-500"
									>Save to your saved items</span
								>
							</h4>
						</div>
						<div class="card-body p-0 d-flex mt-2">
							<i class="feather-lock text-grey-500 me-3 font-lg"></i>
							<h4 class="fw-600 mb-0 text-grey-900 font-xssss mt-0 me-4">
								Unfollow Group
								<span class="d-block font-xsssss fw-500 mt-1 lh-3 text-grey-500"
									>Save to your saved items</span
								>
							</h4>
						</div>
					</div>
				</div>
			</div>

			<div
				v-for="post in posts"
				:key="post"
				class="card w-100 shadow-xss rounded-xxl border-0 p-4 mb-3"
			>
				<div class="card-body p-0 d-flex">
					<figure class="avatar me-3">
						<img
							:src="post.postedUser[0].profilePicture"
							alt="image"
							class="shadow-sm rounded-circle w45"
						/>
					</figure>
					<h4 class="fw-700 text-grey-900 font-xssss mt-1">
						{{ myUser.userName }}
						<span class="d-block font-xssss fw-500 mt-1 lh-3 text-grey-500">{{
							post.createdAt | moment("from", "now")
						}}</span>
					</h4>
					<!-- <h1>{{post._id}}</h1> -->
					<router-link
						class="ms-auto"
						:to="{ name: 'Update', params: { id: post._id } }"
					>
						<v-btn class="ms-auto mr-3">Yenile</v-btn>
					</router-link>
					<v-btn @click="deletePost(post._id)">Sil</v-btn>
					<!-- <a class="ms-auto" id="dropdownMenu5" data-bs-toggle="dropdown" aria-expanded="false"><i class="ti-more-alt text-grey-900 btn-round-md bg-greylight font-xss"></i></a> -->
				</div>

				<div class="card-body p-0 me-lg-5">
					<p class="fw-500 text-grey-500 lh-26 font-xssss w-100 mb-2">
						{{ post.content }}
					</p>
				</div>
				<div v-if="post.type === 'photo'" class="card-body d-block p-0 mb-3">
					<div class="row ps-2 pe-2">
						<div class="col-sm-12 p-1">
							<img
								:src="post.postContent"
								class="rounded-3 w-100"
								alt="image"
							/>
						</div>
					</div>
				</div>
				<div v-if="post.type === 'video'" class="card-body d-block p-0 mb-3">
					<div class="row ps-2 pe-2">
						<div class="col-sm-12 p-1">
							<vuePlayer :src="post.postContent"> </vuePlayer>
						</div>
					</div>
				</div>

				<div class="card-body d-flex p-0">
					<a
						class="
              emoji-bttn
              d-flex
              align-items-center
              fw-600
              text-grey-900 text-dark
              lh-26
              font-xssss
              me-2
            "
					>
						<i
							class="
                feather-thumbs-up
                text-white
                bg-primary-gradiant
                me-1
                btn-round-xs
                font-xss
              "
						></i>
						<!-- <i class="feather-heart text-white bg-red-gradiant me-2 btn-round-xs font-xss"></i> -->

						<v-btn @click="likeOrUnlike(post._id)" mr-2 color="red">{{
							(post.likesFrom.indexOf(userId) != -1 ? "unlike " : "like ") +
								post.likesFrom.length
						}}</v-btn>
					</a>
					<a
						class="
              d-flex
              align-items-center
              fw-600
              text-grey-900 text-dark
              lh-26
              font-xssss
            "
					>
						<i
							class="
                feather-message-circle
                text-dark text-grey-900
                btn-round-sm
                font-lg
              "
						></i>
						<span class="d-none-xss">{{ post.commentCount }} Comment</span>
					</a>
				</div>
			</div>
		</div>
	</div>
</template>

<script>
import globalservice from "../services/globalservice";
import { mapGetters } from "vuex";
import vuePlayer from "@algoz098/vue-player";

export default {
	data: () => ({
		posts: [],
		myUser: null,
		data: {
			content: "",
			type: "text",
			uploadObject: null,
		},
	}),
	components: {
		vuePlayer,
	},
	computed: {
		...mapGetters(["userId", "userName"]),
	},
	methods: {
		createPost() {
			let data = new FormData();
			data.append("content", this.data.content);

			if (this.data.uploadObject === null) {
				data.append("type", "text");
				return globalservice
					.createPost(data)
					.then(() => {
						this.data.content = "";
						globalservice
							.getOwnPosts()
							.then((res) => {
								this.posts = res.data.posts;
							})
							.catch((err) => {
								console.log(err);
							});
					})
					.catch((err) => {
						console.log(err);
					});
			}

			if (this.data.type === "video") {
				data.append("video", this.data.uploadObject);
				data.append("type", this.data.type ?? "text");

				return globalservice
					.createVideoPost(data)
					.then(() => {
						this.data.content = "";
						this.data.uploadObject = null;
						globalservice
							.getOwnPosts()
							.then((res) => {
								this.posts = res.data.posts;
							})
							.catch((err) => {
								console.log(err);
							});
					})
					.catch((err) => {
						console.log(err);
					});
			}
			data.append("image", this.data.uploadObject);
			data.append("type", this.data.type ?? "text");

			return globalservice
				.createPost(data)
				.then(() => {
					this.data.content = "";
					this.data.uploadObject = null;
					globalservice
						.getOwnPosts()
						.then((res) => {
							this.posts = res.data.posts;
						})
						.catch((err) => {
							console.log(err);
						});
				})
				.catch((err) => {
					console.log(err);
				});
		},
		changeType() {
			this.data.type =
				this.data.uploadObject.type === "video/mp4" ? "video" : "photo";
		},
		deletePost(id) {
			globalservice
				.deletePost(id)
				.then(() => {
					// this.snackbarText = "Post Ugurla Silindi";
					// console.log("deleted succesfully");
					// this.snackbar = true
					// const index = this.posts.findIndex((post) => post._id === id);
					// this.posts[index].content = 'deyishdirildi';
					// console.log(this.posts[index].content);
				})
				.catch(() => {
					console.log("delete fail");
					// console.log("salam");

					// this.snackbarText = "Bu mailde account movcud deyil"
					// this.snackbar = true
				})
				.finally(() => {
					const index = this.posts.findIndex((post) => post._id === id);
					console.log(index);
					console.log(this.posts[index].content);
					this.posts = this.posts.filter((post) => post._id !== id);
					// this.posts[index] = null;
					// console.log(this.posts);
				});
		},
		likeOrUnlike(id) {
			globalservice
				.likeOrUnlike(id)
				.then(() => {
					const index = this.posts.findIndex((post) => post._id === id);
					if (this.posts[index].likesFrom.indexOf(this.userId) === -1) {
						this.posts[index].likesFrom.push(this.userId);
					} else {
						console.log(this.posts[index].postedUser[0]._id);
						this.posts[index].likesFrom = this.posts[index].likesFrom.filter(
							(postedId) => postedId !== this.userId
						);
					}
				})
				.catch(() => {
					// this.snackbarText = "Bu mailde account movcud deyil"
					// this.snackbar = true
				});
		},
	},
	created() {
		console.log(this.$route.params);
		globalservice
			.getOwnPosts()
			.then((res) => {
				this.posts = res.data.posts;
			})
			.catch(() => {
				//err
			});
		globalservice
			.getOwnUser()
			.then((res) => {
				this.myUser = res.data.user;
			})
			.catch(() => {});
	},
};
</script>

<style lang="scss" scoped>
.profile-statictic {
	&-icon {
		margin-right: 8px;
	}
	&-text {
		margin-bottom: 0 !important;
	}
}
</style>
