<script>
	import { page } from '$app/state';
	import '../app.css';

	let { children } = $props();

	const links = [
		{ href: '/', label: 'Home' },
		{ href: '/docs', label: 'Docs' },
		{ href: '/terms', label: 'Terms' },
		{ href: '/privacy', label: 'Privacy' },
		{ href: '/about', label: 'About' },
		{ href: '/contact', label: 'Contact' }
	];

	const isHome = $derived(page.url.pathname === '/');
	const navLinks = $derived(isHome ? links.slice(1) : links);
</script>

<nav class="nav">
	<a href="/" class="logo">clioilc</a>
	<div>
		{#each navLinks as link}
			<a href={link.href}>{link.label}</a>
			{#if link !== navLinks[navLinks.length - 1]}&nbsp;&nbsp;{/if}
		{/each}
	</div>
</nav>

<main>
	{@render children()}
</main>

<footer>
	<div class="footer-nav">
		{#each links as link}
			<a href={link.href}>{link.label}</a>
		{/each}
	</div>
	<p>clioilc — observability for AI coding agents</p>
	<p style="margin-top: 0.5rem;">&copy; 2026 clioilc. All rights reserved.</p>
</footer>
