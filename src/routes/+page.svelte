<script>
    // https://rodneylab.com/sveltekit-json-import/
    import projects from '$lib/data/projects.json';
</script>

<!-- TODO add seo via svelte:head -->
 <!-- TODO: split into components -->
  
  <section class="hero">
    <h1>CraftCMS Launchpad</h1>
    <p>Interactive CraftCMS Demos in your browser, powered by DDEV.</p>
  </section>
  
  <section class="container">
    {#each projects as project}
      <div class="card">
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
          {/if}
        </div>
  
        <div class="repo">
          <a href={project.githubRepo} target="_blank">
            <svg fill="none" viewBox="0 0 32 33" width="16" height="16" astro-icon="github">
              <path
                fill="#fff"
                d="M16 2.5c-7.735 0-14 6.265-14 14 0 6.195 4.008 11.427 9.572 13.282.7.123.963-.297.963-.665 0-.332-.018-1.434-.018-2.607-3.517.647-4.427-.858-4.707-1.645-.157-.402-.84-1.645-1.435-1.977-.49-.263-1.19-.91-.018-.928 1.103-.018 1.89 1.015 2.153 1.435 1.26 2.117 3.273 1.523 4.078 1.155.122-.91.49-1.523.892-1.873-3.115-.35-6.37-1.557-6.37-6.912 0-1.523.542-2.783 1.435-3.763-.14-.35-.63-1.785.14-3.71 0 0 1.172-.367 3.85 1.435a12.99 12.99 0 0 1 3.5-.472c1.19 0 2.38.157 3.5.472 2.677-1.82 3.85-1.434 3.85-1.434.77 1.925.28 3.36.14 3.71.893.98 1.435 2.222 1.435 3.762 0 5.372-3.273 6.563-6.387 6.912.507.438.944 1.278.944 2.59 0 1.873-.017 3.378-.017 3.85 0 .368.262.805.962.665A14.022 14.022 0 0 0 30 16.5c0-7.735-6.265-14-14-14Z"
              />
            </svg>
            <span>View source on GitHub</span>
          </a>
        </div>
      </div>
    {/each}
  </section>
  
  <section style="text-align: center; margin-top: 50px;">
    <p style="font-size: 0.9rem;">
      Demo, just for preview purposes. Inspired by <a href="https://astro.new/latest/">astro.new/latest</a>.
    </p>
  </section>


  <style>
    /* TODO: move to global file */ 
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
            padding: 40px;
            max-width: 1200px;
            margin: 0 auto;
        }

        /* Card Styles */
        .card {
            background-color: #1f1f24;
            color: #ccc;
            border-radius: 12px;
            box-shadow: 0 8px 16px rgba(0, 0, 0, 0.3);
            overflow: hidden;
            text-align: center;
            transition: transform 0.3s ease-in-out;
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
        }

        .card p {
            font-size: 0.9em;
            padding: 0 10px;
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
                grid-template-columns: repeat(1, 1fr)
            }

            .hero h1 {
                font-size: 2.5em;
            }

            .hero p {
                font-size: 1em;
            }

            .card{
                margin-bottom: 20px;
            }
        }
  </style>