<script>
	import { GITHUB_URL } from '$lib/site.js';
</script>

<svelte:head>
	<title>Contact — clioilc</title>
</svelte:head>

<div class="page">
	<h1>Contact Us</h1>
	<p class="updated">We'd love to hear from you</p>

	<h2>Get in Touch</h2>
	<p>
		Have a question, feedback, or want to discuss a partnership? Reach out through any
		of the channels below.
	</p>

	<h2>Email</h2>
	<p><a href="mailto:hello@clioilc.com">hello@clioilc.com</a></p>

	<h2>Help with setup</h2>
	<p>
		Most questions are answered in the <a href="/docs">docs</a>, including a
		<a href="/docs#troubleshooting">troubleshooting</a> section with the CLI's error messages.
	</p>

	<h2>Community</h2>
	<p>
		Follow our development, report issues and send pull requests on
		<a href={GITHUB_URL} target="_blank" rel="noopener">GitHub</a>.
	</p>

	<h2>Response Time</h2>
	<p>We typically respond within 1–2 business days.</p>
</div>
