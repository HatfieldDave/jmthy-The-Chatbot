<template>
	<div id="app">
		<!-- If you start to get random styling you don't like, remove container from this div -->

		<nav class="navbar navbar-dark bg-primary">
			<div class="container-fluid">
				<img
					class="logo"
					src="@/assets/JMTHY.png"
					alt=""
					v-on:click="$router.push('home')"
				/>
				<img class="navbar-brand" id="jmthy" src="@/assets/Font.png" alt=""/>
				<button
					class="navbar-toggler"
					type="button"
					data-toggle="collapse"
					data-target="#navbarColor01"
					aria-controls="navbarColor01"
					aria-expanded="false"
					aria-label="Toggle navigation"
				>
					<span class="navbar-toggler-icon"></span>
				</button>
				<div
					class="navbar-collapse collapse"
					id="navbarColor01"
					:key="$route.path"
				>
					<ul class="navbar-nav me-auto">
						<li class="nav-item">
							<router-link class="nav-link" v-bind:to="{ name: 'home' }">
								<i class="fas fa-home"></i>
								<!-- This is a font awesome icon -->
								Home
							</router-link>
							<span class="visually-hidden">(current)</span>
						</li>
						<li class="nav-item">
							<router-link
								class="nav-link"
								v-bind:to="{ name: 'register' }"
								v-if="!$store.state.token"
								>Register</router-link
							>
						</li>
						<li class="nav-item">
							<router-link
								class="nav-link"
								v-bind:to="{ name: 'login' }"
								v-if="!$store.state.token"
								>Login
							</router-link>
						</li>
						<li class="nav-item">
							<router-link
								class="nav-link"
								v-bind:to="{ name: 'logout' }"
								v-if="$store.state.token"
								>Logout
							</router-link>
						</li>
						<li class="nav-item">
							<router-link
								class="nav-link"
								v-bind:to="{ name: 'Greeting' }"
								v-if="$store.state.token"
								>Chat
							</router-link>
						</li>
					</ul>
				</div>
			</div>
		</nav>
		<router-view class="body" />
	</div>
</template>

<script>
export default {};
</script>

<!-- Application-Wide Styles go here. 
     Any valid CSS or SCSS is allowable here. See https://sass-lang.com/documentation/style-rules for info on SCSS -->
<style lang="scss">
#app {
	height: 100vh;
	display: grid;
	grid-template-areas:
		"header"
		"body";
	grid-template-rows: 1fr 10fr;
}
.logo {
	width: 100px;
}
.body {
	grid-area: body;
}
.navbar {
	grid-area: header;
}
#jmthy{
	max-width: 15%;
}
.navbar-brand {
	letter-spacing: 0.5rem;
	font-weight: 900;
}
.nav-item {
	text-align: right;
}

@import "./styles/colors.scss";

// Import the bootstrap styles. If you want to override Bootstrap colors, it needs to happen above this line
@import "../node_modules/bootstrap/scss/bootstrap";

// Your custom styles go below this point
//@import "_bootswatch.scss";
@import url("https://www.fontspace.com/friendly-smiley-font-f65855");
</style>
