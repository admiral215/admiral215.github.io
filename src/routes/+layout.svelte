<script lang="ts">
	import '../app.css';

	let { children } = $props();
</script>

<svelte:head>
	<link rel="icon" href="/favicon.ico" />
    <meta name="google-site-verification" content="2o9Bll_NAFdNl9_NRHYTx9GD91Qf6-PC-B0JsQPPqIE" />
    <title>Rully Admiral - Software Engineer | Portfolio</title>
    <meta name="description" content="Software Engineer with 3+ years experience in Go, Java, and Javascript Frontend Framework. Open to new opportunities in web and mobile development." />
    <meta name="keywords" content="software engineer, backend developer, web developer, mobile developer, looking for job, open to work" />
    <meta name="author" content="Rully Admiral" />

    <meta property="og:type" content="website" />
    <meta property="og:url" content="https://admiral215.github.io/" />
    <meta property="og:title" content="Rully Admiral - Software Engineer" />
    <meta property="og:description" content="Experienced Software Engineer specializing in modern web and mobile technologies. Check out my projects and let's connect!" />
    <meta property="og:image" content="https://avatars.githubusercontent.com/u/101520167?v=4" />
    <meta property="og:image:width" content="1200" />
    <meta property="og:image:height" content="630" />

    <meta name="twitter:card" content="summary_large_image" />
    <meta name="twitter:title" content="Rully Admiral - Software Engineer" />
    <meta name="twitter:description" content="Software Engineer open to new opportunities" />
    <meta name="twitter:image" content="https://avatars.githubusercontent.com/u/101520167?v=4" />

    <link rel="canonical" href="https://admiral215.github.io/" />
    <link rel="icon" href="/favicon.ico" />
</svelte:head>

{@render children?.()}
