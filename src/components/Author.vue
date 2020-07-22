<template>
	<div class="author">
	<div class="author__sticky">
		<g-image alt="Author image" class="author__image" src="~/assets/images/author.jpg" width="190" height="190" blur="5" quality="100"/>

		<h1 v-if="showTitle" class="author__site-title">
			Sohaib Sherif
		</h1>

		<p class="author__intro">
			{{ $static.metadata.tagLine }}
		</p>

		<p class="author__links">
			<a href="https://www.linkedin.com/in/sohaib-sherif" target="__blank" rel="noopener noreferrer" title="LinkedIn">
				<svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="feather feather-linkedin"><path d="M16 8a6 6 0 0 1 6 6v7h-4v-7a2 2 0 0 0-2-2 2 2 0 0 0-2 2v7h-4v-7a6 6 0 0 1 6-6z"></path><rect x="2" y="9" width="4" height="12"></rect><circle cx="4" cy="4" r="2"></circle></svg>
			</a>
			<a href="https://github.com/Sohaib-Sherif" target="__blank" rel="noopener noreferrer" title="Github">
				<svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="feather feather-github"><path d="M9 19c-5 1.5-5-2.5-7-3m14 6v-3.87a3.37 3.37 0 0 0-.94-2.61c3.14-.35 6.44-1.54 6.44-7A5.44 5.44 0 0 0 20 4.77 5.07 5.07 0 0 0 19.91 1S18.73.65 16 2.48a13.38 13.38 0 0 0-7 0C6.27.65 5.09 1 5.09 1A5.07 5.07 0 0 0 5 4.77a5.44 5.44 0 0 0-1.5 3.78c0 5.42 3.3 6.61 6.44 7A3.37 3.37 0 0 0 9 18.13V22"></path></svg>
			</a>
			<a href="https://sohaib-sherif.github.io/resume/" target="__blank" rel="noopener noreferrer" title="Resume">
				<svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="feather feather-file-text"><path d="M14 2H6a2 2 0 0 0-2 2v16a2 2 0 0 0 2 2h12a2 2 0 0 0 2-2V8z"></path><polyline points="14 2 14 8 20 8"></polyline><line x1="16" y1="13" x2="8" y2="13"></line><line x1="16" y1="17" x2="8" y2="17"></line><polyline points="10 9 9 9 8 9"></polyline></svg>
			</a>
		</p>
	</div>
	</div>
</template>

<static-query>
query {
  metadata {
    siteName,
	siteDescription,
	tagLine,
  }
}
</static-query>

<script>
export default {
	props: ['showTitle']
}
</script>

<style lang="scss">
.author {
	margin: 0 3em 0 0;
	max-width: 500px;
	text-align: center;
	padding: calc(var(--space) / 2) 0;
	flex: 1;

	&__image {
		border-radius: 100%;
		width: 180px;
		height: 180px;
		margin-bottom: 1em;
	}

	&__intro {
		opacity: .8;
	}

	&__site-title {
		font-size: 1.5em;
	}

	&__links {
		
		margin-top: -.5em;
		svg {
			margin: 0 .5em;
		}
		> a {
			color: currentColor;
		}
	}

	&__sticky {
		position: sticky;
		top: 1em;
	}
}
</style>
