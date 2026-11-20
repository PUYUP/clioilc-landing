<script>
	import { DASH_URL, TRACKER_REPO } from '$lib/site.js';
</script>

<svelte:head>
	<title>About — clioilc</title>
</svelte:head>

<div class="page">
	<h1>About clioilc</h1>
	<p class="updated">Observability for AI coding agents</p>

	<h2>Our Mission</h2>
	<p>
		AI coding agents now write, run and fix a large share of the code we ship. When an agent
		works for an hour, the final diff tells you little about what it actually did, where it got
		stuck, or what it cost. clioilc exists to make that work visible.
	</p>

	<h2>What We Do</h2>
	<p>
		clioilc reads the session logs your agent already keeps on your machine and turns them into
		a clear record: every prompt, reply and tool call, which ones failed and why, the tokens used
		and what they would cost on the API, per project, model and day. You can read it in the
		terminal, or sync it to your dashboard at <a href={DASH_URL}>{DASH_URL.replace('https://', '')}</a>.
	</p>
	<p>
		We start with Claude Code. Support for Gemini CLI and Codex is on the way, and readers for
		other agents are plugins anyone can write.
	</p>

	<h2>Why It Matters</h2>
	<ul>
		<li><strong>Transparency</strong> — see what your agent did, step by step, not just the final diff</li>
		<li><strong>Quality</strong> — spot failing tool calls and API errors as they happen</li>
		<li><strong>Cost</strong> — know which projects and models your tokens go to</li>
		<li><strong>Privacy</strong> — your prompts and replies stay yours, encrypted end-to-end if you choose</li>
	</ul>

	<h2>Open Source</h2>
	<p>
		The <code>clioilc</code> CLI that runs on your machine is open source, so you can check
		exactly what it reads and what it sends: <a href={TRACKER_REPO}>{TRACKER_REPO.replace('https://', '')}</a>.
	</p>

	<h2>Get in Touch</h2>
	<p>Have questions or want to learn more? Read the <a href="/docs">docs</a> or <a href="/contact">contact us</a>.</p>
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
