<script>
	import { DASH_URL } from '$lib/site.js';
</script>

<svelte:head>
	<title>Terms of Service — clioilc</title>
</svelte:head>

<div class="page">
	<h1>Terms of Service</h1>
	<p class="updated">Last updated: November 20, 2026</p>

	<h2>1. Acceptance of Terms</h2>
	<p>
		By accessing or using clioilc ("the Service"), you agree to be bound by these Terms of
		Service. If you do not agree, do not use the Service.
	</p>

	<h2>2. Description of Service</h2>
	<p>
		clioilc is an observability platform for AI coding agents, currently Claude Code and Devin
		CLI. It consists of the <code>clioilc</code> command-line tool, which reads your agents' local
		history and uploads it to your account, and the dashboard at
		<a href={DASH_URL}>{DASH_URL.replace('https://', '')}</a>, which provides analytics,
		statistics, cost estimates and an activity timeline. Cost figures are estimates at public
		API prices, not invoices.
	</p>

	<h2>3. Acceptable Use</h2>
	<p>You agree not to:</p>
	<ul>
		<li>Use the Service for any unlawful purpose</li>
		<li>Attempt to gain unauthorized access to the Service or its systems</li>
		<li>Interfere with or disrupt the integrity or performance of the Service</li>
		<li>
			Reverse engineer, decompile, or disassemble any part of the Service, except components
			published as open source, which are governed by their own licenses
		</li>
	</ul>

	<h2>4. Intellectual Property</h2>
	<p>
		The Service and its original content, features, and functionality are owned by clioilc
		and are protected by international copyright, trademark, and other intellectual property
		laws.
	</p>

	<h2>5. Limitation of Liability</h2>
	<p>
		The Service is provided "as is" without warranties of any kind. To the maximum extent
		permitted by law, clioilc shall not be liable for any indirect, incidental, or
		consequential damages arising from your use of the Service.
	</p>

	<h2>6. Changes to Terms</h2>
	<p>
		We may modify these terms at any time. Continued use of the Service after changes
		constitutes acceptance of the revised terms.
	</p>

	<h2>7. Contact</h2>
	<p>Questions about these Terms? <a href="/contact">Contact us</a>.</p>
</div>

<style>
	code {
		font-family: 'SF Mono', Menlo, Consolas, monospace;
		font-size: 0.85em;
		background: var(--card);
		border: 1px solid var(--border);
		border-radius: 6px;
		padding: 0.05rem 0.35rem;
	}
</style>
