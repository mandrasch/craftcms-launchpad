<script>
	// https://rodneylab.com/sveltekit-json-import/
	import projects from '$lib/data/projects.json';
</script>

<svelte:head>
	<title>CraftCMS Launchpad</title>
	<meta name="description" content="Interactive CraftCMS demos in your browser, powered by DDEV." />
</svelte:head>

<section class="hero">
	<h1>CraftCMS Launchpad</h1>
	<p>Interactive CraftCMS demos in your browser, powered by DDEV.</p>
</section>

<section class="container">
	{#each projects as project}
		<div class={`card ${project.workInProgress ? 'card--progress' : ''}`}>
			<div class="card-container">
				<img src={project.image} alt={project.title} />
				<h2>{project.title}</h2>
				<p>{project.description}</p>

				<div class="btn-container">
					{#if project.gitpodUrl}
						<a href={project.gitpodUrl} class="btn btn--gitpod" target="_blank">
							<img src="https://gitpod.io/button/open-in-gitpod.svg" alt="Open in Gitpod" />
						</a>
					{/if}

					{#if project.codespacesUrl}
						<a href={project.codespacesUrl} class="btn btn--codespaces" target="_blank">
							<img src="https://github.com/codespaces/badge.svg" alt="Open in GitHub Codespaces" />
						</a>
					{:else}
						<!-- placeholder, should be done better with min-height ;) -->
						<div style="height:30px;"></div>
					{/if}
				</div>

				<div class="repo">
					<a href={project.githubRepo} target="_blank">
						<svg fill="none" viewBox="0 0 32 33" width="16" height="16">
							<path
								fill="#fff"
								d="M16 2.5c-7.735 0-14 6.265-14 14 0 6.195 4.008 11.427 9.572 13.282.7.123.963-.297.963-.665 0-.332-.018-1.434-.018-2.607-3.517.647-4.427-.858-4.707-1.645-.157-.402-.84-1.645-1.435-1.977-.49-.263-1.19-.91-.018-.928 1.103-.018 1.89 1.015 2.153 1.435 1.26 2.117 3.273 1.523 4.078 1.155.122-.91.49-1.523.892-1.873-3.115-.35-6.37-1.557-6.37-6.912 0-1.523.542-2.783 1.435-3.763-.14-.35-.63-1.785.14-3.71 0 0 1.172-.367 3.85 1.435a12.99 12.99 0 0 1 3.5-.472c1.19 0 2.38.157 3.5.472 2.677-1.82 3.85-1.434 3.85-1.434.77 1.925.28 3.36.14 3.71.893.98 1.435 2.222 1.435 3.762 0 5.372-3.273 6.563-6.387 6.912.507.438.944 1.278.944 2.59 0 1.873-.017 3.378-.017 3.85 0 .368.262.805.962.665A14.022 14.022 0 0 0 30 16.5c0-7.735-6.265-14-14-14Z"
							/>
						</svg>
						<span>View source on GitHub</span>
					</a>
				</div>
			</div>
		</div>
	{/each}
</section>

<section class="footer" style="text-align: center; margin-top: 50px;">
	<p>
		Please note that GitHub Codespaces can be a bit buggy on startup / launches; use Gitpod for best
		experience.
	</p>
	<p>
		Inspired by <a href="https://astro.new/latest/">astro.new/latest</a>. |
		<a href="https://matthias-andrasch.eu/impressum-datenschutz/">Imprint & Privacy</a>
	</p>
</section>

<a
	href="https://github.com/mandrasch/craftcms-launchpad"
	class="github-corner"
	aria-label="View source on GitHub"
	><svg
		width="80"
		height="80"
		viewBox="0 0 250 250"
		style="fill:#fff; color:#151513; position: absolute; top: 0; border: 0; right: 0;"
		aria-hidden="true"
		><path d="M0,0 L115,115 L130,115 L142,142 L250,250 L250,0 Z"></path><path
			d="M128.3,109.0 C113.8,99.7 119.0,89.6 119.0,89.6 C122.0,82.7 120.5,78.6 120.5,78.6 C119.2,72.0 123.4,76.3 123.4,76.3 C127.3,80.9 125.5,87.3 125.5,87.3 C122.9,97.6 130.6,101.9 134.4,103.2"
			fill="currentColor"
			style="transform-origin: 130px 106px;"
			class="octo-arm"
		></path><path
			d="M115.0,115.0 C114.9,115.1 118.7,116.5 119.8,115.4 L133.7,101.6 C136.9,99.2 139.9,98.4 142.2,98.6 C133.8,88.0 127.5,74.4 143.8,58.0 C148.5,53.4 154.0,51.2 159.7,51.0 C160.3,49.4 163.2,43.6 171.4,40.1 C171.4,40.1 176.1,42.5 178.8,56.2 C183.1,58.6 187.2,61.8 190.9,65.4 C194.5,69.0 197.7,73.2 200.1,77.6 C213.8,80.2 216.3,84.9 216.3,84.9 C212.7,93.1 206.9,96.0 205.4,96.6 C205.1,102.4 203.0,107.8 198.3,112.5 C181.9,128.9 168.3,122.5 157.7,114.1 C157.9,116.9 156.7,120.9 152.7,124.9 L141.0,136.5 C139.8,137.7 141.6,141.9 141.8,141.8 Z"
			fill="currentColor"
			class="octo-body"
		></path></svg
	></a
>

<style>
	/* TODO: move to global file */

	:global(*, *::before, *::after) {
		padding: 0;
		margin: 0;
		box-sizing: border-box;
	}

	:global(body) {
		font-family: 'Helvetica Neue', sans-serif;
		margin: 0;
		padding: 0;
		box-sizing: border-box;
		color: #ffffff;
		background: linear-gradient(135deg, #1a1a2e, #16213e, #0f3460);
		position: relative;
	}

	/* Hero Section */
	.hero {
		position: relative;
		color: white;
		text-align: center;
		padding: 100px 20px 20px 20px;
		overflow: hidden;
	}

	.hero h1 {
		font-size: 3.5em;
		font-weight: 500;
		margin: 0;
		z-index: 1;
		position: relative;
	}

	.hero p {
		font-size: 1.2em;
		margin-top: 10px;
		z-index: 1;
		position: relative;
		font-weight: 300;
	}

	/* Container for Cards */
	.container {
		display: grid;
		grid-template-columns: repeat(3, 1fr);
		gap: 20px;
		row-gap: 40px;
		padding: 40px;
		max-width: 1200px;
		margin: 0 auto;
	}

	/* Card Styles */
	.card {
		position: relative;
		overflow: visible;
		background-color: #1f1f24;
		color: #ccc;
		border-radius: 12px;
		box-shadow: 0 8px 16px rgba(0, 0, 0, 0.3);
		text-align: center;
		transition: transform 0.3s ease-in-out;
		width: 100%;
		height: 100%;
	}

	.card-container {
		width: 100%;
		height: 100%;
		display: flex;
		flex-direction: column;
		justify-content: space-between;
	}

	/*.card:hover {
      transform: translateY(-10px);
    }*/

	.card img {
		width: 100%;
		height: 200px;
		object-fit: cover;
	}

	.card h2 {
		font-size: 1.2em;
		margin: 35px 0 5px;
		padding: 0 10px;
		font-weight: normal;
		align-items: flex-start;
	}

	.card p {
		font-size: 0.9em;
		padding: 0 20px;
		margin-bottom: 30px;
	}

	.card .repo {
		padding: 10px 10px;
		border-top: 1px solid #333;
	}

	.card .repo a {
		color: white;
		font-size: 0.75rem;
		text-decoration: none;
		display: flex;
		justify-content: center;
		align-items: center;
		gap: 5px;
	}

	/* Button Styles */
	.btn-container {
		display: flex;
		flex-direction: column;
		gap: 10px;
		justify-content: center;
		margin-bottom: 20px;
	}

	.btn {
		padding: 0;
		border: none;
		cursor: pointer;
		max-height: 90px;
		margin: 0 auto;
		text-align: center;
		background: none;
	}

	.btn img {
		height: auto;
		width: auto;
		border-radius: 8px;
	}

	.btn--codespaces {
		max-width: 80%;
	}

	.btn--codespaces img {
		max-width: 85%;
	}

	/* Responsive Layout */
	@media (max-width: 1200px) {
		.container {
			grid-template-columns: repeat(3, 1fr);
		}
	}

	@media (max-width: 768px) {
		.container {
			grid-template-columns: repeat(2, 1fr);
		}
	}

	@media (max-width: 640px) {
		.container {
			grid-template-columns: repeat(1, 1fr);
		}

		.hero h1 {
			font-size: 2.5em;
		}

		.hero p {
			font-size: 1em;
		}

		.card {
			margin-bottom: 20px;
		}
	}

	/* https://codepen.io/sudeepgumaste/pen/mdevOQq */
	.card.card--progress::before {
		position: absolute;
		top: 2rem;
		right: -0.5rem;
		content: '';
		background: orange;
		height: 28px;
		width: 28px;
		transform: rotate(45deg);
		z-index: -1;
	}

	.card.card--progress::after {
		position: absolute;
		content: 'Work in progress';
		top: 11px;
		right: -14px;
		padding: 0.5rem;
		width: 10rem;
		background: orange;
		color: #333;
		text-align: center;
		font-family: 'Roboto', sans-serif;
		box-shadow: 4px 4px 15px rgba(26, 35, 126, 0.2);
	}

	.footer {
		margin: 80px 0 25px;
	}
	.footer a {
		color: white;
	}
	.footer p {
		font-size: 0.9rem;
		margin-bottom: 20px;
	}

	.github-corner:hover .octo-arm {
		animation: octocat-wave 560ms ease-in-out;
	}
	@keyframes octocat-wave {
		0%,
		100% {
			transform: rotate(0);
		}
		20%,
		60% {
			transform: rotate(-25deg);
		}
		40%,
		80% {
			transform: rotate(10deg);
		}
	}
	@media (max-width: 500px) {
		.github-corner:hover .octo-arm {
			animation: none;
		}
		.github-corner .octo-arm {
			animation: octocat-wave 560ms ease-in-out;
		}
	}
</style>
