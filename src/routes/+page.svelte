<script>
    import Main from '../components/Main.svelte';
    import { base } from '$app/paths';
    
    const siteUrl = 'https://tomasalvarez0.github.io/my-portfolio';
    const title = 'Tomás Álvarez | Systems Engineering Student & Developer';
    const description = 'Systems Engineering student passionate about technology and sports. Explore my projects, skills, and academic achievements. Currently pursuing a degree in Systems Engineering.';
</script>

<svelte:head>
    <title>{title}</title>
    <meta name="description" content={description} />
    <meta name="keywords" content="Tomás Álvarez, Systems Engineering, Developer, Portfolio, Svelte, SvelteKit, Technology, Argentina" />
    <meta name="author" content="Tomás Álvarez" />
    
    <!-- Open Graph / Facebook -->
    <meta property="og:type" content="website" />
    <meta property="og:url" content={siteUrl} />
    <meta property="og:title" content={title} />
    <meta property="og:description" content={description} />
    <meta property="og:image" content={`${siteUrl}${base}/images/profile.png`} />
    <meta property="og:site_name" content="Tomás Álvarez Portfolio" />
    
    <!-- Twitter -->
    <meta name="twitter:card" content="summary_large_image" />
    <meta name="twitter:url" content={siteUrl} />
    <meta name="twitter:title" content={title} />
    <meta name="twitter:description" content={description} />
    <meta name="twitter:image" content={`${siteUrl}${base}/images/profile.png`} />
    
    <!-- Additional Meta Tags -->
    <meta name="robots" content="index, follow" />
    <meta name="theme-color" content="#7c3aed" />
    <link rel="canonical" href={siteUrl} />
</svelte:head>

<Main />    