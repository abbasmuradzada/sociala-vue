<template>
	<div>
		<!-- <div class="preloader"></div> -->
		<div class="main-wrap">
			<div class="nav-header bg-transparent shadow-none border-0">
				<div class="nav-top w-100">
					<a href="index.html"
						><i class="feather-zap text-success display1-size me-2 ms-0"></i
						><span
							class="d-inline-block fredoka-font ls-3 fw-600 text-current font-xxl logo-text mb-0"
							>Sociala.
						</span>
					</a>
					<!-- <a href="#" class="mob-menu ms-auto me-2 chat-active-btn"><i class="feather-message-circle text-grey-900 font-sm btn-round-md bg-greylight"></i></a> -->
					<!-- <a href="default-video.html" class="mob-menu me-2"><i class="feather-video text-grey-900 font-sm btn-round-md bg-greylight"></i></a> -->
					<!-- <a href="#" class="me-2 menu-search-icon mob-menu"><i class="feather-search text-grey-900 font-sm btn-round-md bg-greylight"></i></a> -->
					<!-- <button class="nav-menu me-0 ms-2"></button> -->
					<!-- <a href="#" class="header-btn d-none d-lg-block bg-current fw-500 text-white font-xsss p-3 ms-2 w100 text-center lh-20 rounded-xl"  data-bs-toggle="modal" data-bs-target="#Modalregister">Register</a> -->

					<a
						@click="goToRegister"
						class="header-btn d-none cursor-pointer d-lg-block bg-primary bg-current fw-500 text-white font-xsss p-3 ms-auto w100 text-center lh-20 rounded-xl"
						data-bs-toggle="modal"
						data-bs-target="#Modallogin"
						>Register</a
					>
					<!-- <a href="#" class="header-btn d-none d-lg-block bg-current fw-500 text-white font-xsss p-3 ms-2 w100 text-center lh-20 rounded-xl"  data-bs-toggle="modal" data-bs-target="#Modalregister">Register</a> -->
				</div>
			</div>

			<div class="row">
				<div
					class="col-xl-5 d-none d-xl-block p-0 vh-100 bg-image-cover bg-no-repeat"
				></div>
				<div
					class="col-xl-7 vh-100 align-items-center d-flex bg-white rounded-3 overflow-hidden"
				>
					<div class="card shadow-none border-0 ms-auto me-auto login-card">
						<div class="card-body rounded-0 text-left">
							<h2 class="fw-700 display1-size display2-md-size mb-3">
								Login into <br />your account
							</h2>
							<form @submit.prevent="submit()">
								<div class="form-group icon-input mb-3">
									<i class="font-sm ti-email text-grey-500 pe-0"></i>
									<input
										v-model="email"
										type="text"
										class="style2-input ps-5 form-control text-grey-900 font-xsss fw-600"
										placeholder="enter username or email"
									/>
								</div>
								<div class="form-group icon-input mb-1">
									<input
										v-model="password"
										type="Password"
										class="style2-input ps-5 form-control text-grey-900 font-xss ls-3"
										placeholder="Password"
									/>
									<i class="font-sm ti-lock text-grey-500 pe-0"></i>
								</div>
								<div class="form-check text-left mb-3">
									<input
										type="checkbox"
										class="form-check-input mt-2"
										id="exampleCheck5"
									/>
									<label
										class="form-check-label font-xsss text-grey-500"
										for="exampleCheck5"
										>Remember me</label
									>
									<a
										@click="goToForgetPass()"
										class="fw-600 font-xsss text-grey-700 mt-1 float-right"
										>Forgot your Password?</a
									>
								</div>
								<div class="form-group mb-1">
									<button
										type="submit"
										class="form-control text-center style2-input text-white fw-600 bg-dark border-0 p-0 "
									>
										Login
									</button>
								</div>
							</form>

							<div class="col-sm-12 p-0 text-left">
								<h6 class="text-grey-500 font-xsss fw-500 mt-0 mb-0 lh-32">
									Dont have account
									<a @click="goToRegister" class="fw-700 ms-1 cursor-pointer"
										>Register</a
									>
								</h6>
							</div>
						</div>
					</div>
				</div>
			</div>
			<v-snackbar v-model="snackbar">
				{{ snackbarText }}
				<template v-slot:action="{ attrs }">
					<v-btn color="pink" text v-bind="attrs" @click="snackbar = false">
						close
					</v-btn>
				</template>
			</v-snackbar>
		</div>
	</div>
</template>

<script>
import { mapGetters } from "vuex";
export default {
	data: () => ({
		email: "hasan@code.edu.az",
		password: "123456",
		userName: null,
		snackbarText: "xanalari doldurun",
		snackbar: false,
	}),
	computed: {
		...mapGetters(["isAuthenticated"]),
	},
	methods: {
		goToRegister() {
			this.$router.push({ name: "Register" });
		},
		goToForgetPass() {
			this.$router.push({ name: "ForgetPassword" });
		},
		async submit() {
			if (this.email.length < 1 || this.password.length < 1) {
				console.log("failed login");
				this.snackbarText = "xanalari doldurun";
				this.snackbar = true;
			} else {
				let emailRegex = /\S+@\S+\.\S+/;
				if (!emailRegex.test(this.email)) {
					this.userName = this.email;
					this.email = null;
				}
				return new Promise((resolve, reject) => {
					this.$store
						.dispatch("login", {
							email: this.email,
							password: this.password,
							userName: this.userName,
						})
						.then((res) => {
							resolve(res);
							if (this.isAuthenticated) {
								console.log("aa");
								const { query } = this.$router.currentRoute;
								this.$router.push(query.redirect ? query.redirect : "/");
							}
						})
						.catch((err) => {
							this.snackbarText = "email ve ya shifre yanlish daxil edilib";
							this.snackbar = true;
							this.email = "";
							this.password = "";
							reject(err);
						});
				});
			}
		},
	},
};
</script>

<style lang="scss" scoped>
.bg-image-cover {
	background-image: url(../assets/images/login-bg.jpg);
}
</style>
