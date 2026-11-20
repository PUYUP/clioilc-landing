<script>
	import { DASH_URL, TRACKER_REPO } from '$lib/site.js';

	const dash = DASH_URL.replace('https://', '');
</script>

<svelte:head>
	<title>clioilc — See what your AI coding agent did</title>
	<meta
		name="description"
		content="Every prompt, reply, tool call, error and dollar your AI coding agent spends, in one dashboard. Starting with Claude Code."
	/>
</svelte:head>

<header class="hero">
	<span class="badge">Observability for AI coding agents</span>
	<h1 class="logo">clioilc</h1>
	<p class="tagline">
		See what your AI coding agent did — every prompt, reply, tool call, error and dollar — in one
		dashboard. Starting with Claude Code.
	</p>
	<div class="cta">
		<a class="btn btn-primary" href="/docs">Start Tracking</a>
		<a class="btn btn-ghost" href="#features">What you get</a>
	</div>
</header>

<section id="agents">
	<p class="section-label">Supported Agents</p>
	<h2>Built for Claude Code, open to more</h2>
	<p class="section-sub">
		clioilc reads the session logs your agent already writes on your machine. Nothing to wrap, no
		proxy in between.
	</p>
	<div class="agents">
		<div class="agent">
			<h3><span class="dot" style="background:#d97757"></span>Claude Code</h3>
			<p><strong>Supported.</strong> Tokens, cost, prompts, replies, thinking and every tool call.</p>
		</div>
		<div class="agent">
			<h3><span class="dot" style="background:#4285f4"></span>Gemini CLI</h3>
			<p>Coming soon.</p>
		</div>
		<div class="agent">
			<h3><span class="dot" style="background:#10a37f"></span>Codex</h3>
			<p>Coming soon.</p>
		</div>
		<div class="agent">
			<h3><span class="dot" style="background:#999999"></span>Your agent</h3>
			<p>
				Readers are plugins: <code>clioilc add mod &lt;name&gt;</code> scaffolds one.
				<a href={TRACKER_REPO}>See the source</a>.
			</p>
		</div>
	</div>
</section>

<section id="how-it-works">
	<p class="section-label">How It Works</p>
	<h2>Three steps to full visibility</h2>
	<p class="section-sub">
		About ten minutes from install to your first day in the dashboard.
		<a href="/docs">Read the full guide</a>.
	</p>
	<div class="steps">
		<div class="step">
			<div class="step-number">1</div>
			<h3>Install the CLI</h3>
			<p>
				<code>cargo install</code> the <code>clioilc</code> CLI and import your Claude Code history.
				Try <code>clioilc activity</code> in the terminal before anything leaves your machine.
			</p>
		</div>
		<div class="step">
			<div class="step-number">2</div>
			<h3>Connect your machine</h3>
			<p>
				Run <code>clioilc login</code>, approve the code in your browser, and pick server-side or
				end-to-end encryption. <code>clioilc service install</code> keeps it syncing in the
				background.
			</p>
		</div>
		<div class="step">
			<div class="step-number">3</div>
			<h3>See it in the dashboard</h3>
			<p>
				Open <a href={DASH_URL}>{dash}</a>: cost, tokens, errors and a timeline of every session,
				updated within about 30 seconds.
			</p>
		</div>
	</div>
</section>

<section id="features">
	<p class="section-label">Features</p>
	<h2>What you get</h2>
	<p class="section-sub">Everything comes from your agent's own logs, so nothing is estimated from guesses.</p>
	<div class="features">
		<div class="feature">
			<div class="icon">💸</div>
			<h3>Cost by project and model</h3>
			<p>
				What your tokens would cost on the Claude API, priced per message at the rate of the day,
				per hour or day and broken down by project and model.
			</p>
		</div>
		<div class="feature">
			<div class="icon">⏱️</div>
			<h3>Session timeline</h3>
			<p>
				Every prompt, reply, thinking block and tool call, grouped by session. Filter by type,
				status or project, or search the text.
			</p>
		</div>
		<div class="feature">
			<div class="icon">⚠️</div>
			<h3>Errors at a glance</h3>
			<p>
				A year-long calendar of successful and failed tool calls. Click a day to jump straight to
				what went wrong, with the error output.
			</p>
		</div>
		<div class="feature">
			<div class="icon">🔒</div>
			<h3>Private by design</h3>
			<p>
				Secrets are redacted on your machine. Statistics carry no paths or text, and your prompts
				and replies are encrypted, end-to-end if you choose.
			</p>
		</div>
		<div class="feature">
			<div class="icon">💻</div>
			<h3>Every machine, one account</h3>
			<p>
				Connect each laptop with one login; the same project counts once. See which machines are
				active, and revoke any of them.
			</p>
		</div>
		<div class="feature">
			<div class="icon">⌨️</div>
			<h3>Works in the terminal too</h3>
			<p>
				<code>clioilc activity</code> and <code>clioilc usage report</code> show the same data
				locally, with or without an account.
			</p>
		</div>
	</div>
</section>

<style>
	.agent p strong { color: var(--fg); }
	.agent a,
	.section-sub a,
	.step a { color: var(--fg); }
	.agent code,
	.feature code {
		font-family: 'SF Mono', Menlo, Consolas, monospace;
		font-size: 0.78rem;
		background: var(--card);
		border: 1px solid var(--border);
		border-radius: 6px;
		padding: 0.05rem 0.35rem;
		white-space: nowrap;
	}
	.agent code { background: #fff; }
</style>
