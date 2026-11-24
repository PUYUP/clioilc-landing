<script>
	import { DASH_URL, TRACKER_REPO } from '$lib/site.js';

	const dash = DASH_URL.replace('https://', '');
</script>

<svelte:head>
	<title>clioilc — See what your AI coding agent did</title>
	<meta
		name="description"
		content="Every prompt, reply, tool call, error and dollar your AI coding agents spend, in one dashboard, anchored to your git history. Claude Code and Devin today."
	/>
</svelte:head>

<header class="hero">
	<span class="badge">Observability for AI coding agents</span>
	<h1 class="logo">clioilc</h1>
	<p class="tagline">
		See what your AI coding agents did — every prompt, reply, tool call, error and dollar — in one
		dashboard, tied to the commits and pull requests they produced. Claude Code and Devin today.
	</p>
	<div class="cta">
		<a class="btn btn-primary" href="/docs">Start Tracking</a>
		<a class="btn btn-ghost" href="#features">What you get</a>
	</div>
</header>

<section id="agents">
	<p class="section-label">Supported Agents</p>
	<h2>One record for every agent you use</h2>
	<p class="section-sub">
		clioilc reads the history your agents already keep on your machine. Nothing to wrap, no proxy
		in between, and every agent lands in the same dashboard, so you can compare them.
	</p>
	<div class="agents">
		<div class="agent">
			<h3><span class="dot" style="background:#d97757"></span>Claude Code</h3>
			<p><strong>Supported.</strong> Tokens, cost, prompts, replies, thinking and every tool call.</p>
		</div>
		<div class="agent">
			<h3><span class="dot" style="background:#14a38b"></span>Devin CLI</h3>
			<p>
				<strong>Supported.</strong> Read from its local session database, read-only. Same
				timeline, same journal, priced at the SWE model rates.
			</p>
		</div>
		<div class="agent">
			<h3><span class="dot" style="background:#4285f4"></span>Antigravity</h3>
			<p>Coming soon.</p>
		</div>
		<div class="agent">
			<h3><span class="dot" style="background:#10a37f"></span>Codex</h3>
			<p>Coming soon.</p>
		</div>
		<div class="agent">
			<h3><span class="dot" style="background:#999999"></span>Your agent</h3>
			<p>
				Readers are plugins with a written contract: <code>clioilc add mod &lt;name&gt;</code>
				scaffolds one. <a href={`${TRACKER_REPO}/blob/main/docs/readers.md`}>Reader contract</a>.
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
				<code>cargo install</code> the <code>clioilc</code> CLI and import your Claude Code or Devin
				history.
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
	<p class="section-sub">Everything comes from your agents' own logs and your git history, so nothing is estimated from guesses.</p>
	<div class="features">
		<div class="feature">
			<div class="icon">📓</div>
			<h3>A journal anchored to git</h3>
			<p>
				Work items, not just sessions: what was asked, which commits and pull requests came out,
				what is still uncommitted, and what keeps failing. Copy one as a PR description.
			</p>
		</div>
		<div class="feature">
			<div class="icon">💸</div>
			<h3>Cost by project, model and agent</h3>
			<p>
				What your tokens would cost at API rates, priced per message, broken down by project,
				model and agent. Monthly budgets per project warn you before you go over.
			</p>
		</div>
		<div class="feature">
			<div class="icon">🧮</div>
			<h3>Plans against real use</h3>
			<p>
				Tell clioilc what you pay (Claude Max, Devin Pro, …) and see whether the plan pays off this
				month, or which plan would cost less.
			</p>
		</div>
		<div class="feature">
			<div class="icon">🎛️</div>
			<h3>Filter by model</h3>
			<p>
				Pick one or more models on any page. Reports, costs and timelines follow, so you can
				compare what each model delivered and what it cost.
			</p>
		</div>
		<div class="feature">
			<div class="icon">📄</div>
			<h3>Client-ready reports</h3>
			<p>
				A work report per project and period, with delivery, time and (if you want) AI cost. Print
				it, save it as PDF or export CSV. Prompts never appear in it.
			</p>
		</div>
		<div class="feature">
			<div class="icon">⏱️</div>
			<h3>Session timeline and search</h3>
			<p>
				Every prompt, reply, thinking block and tool call, with the model, the person and the
				device behind it. Search your whole history in the browser.
			</p>
		</div>
		<div class="feature">
			<div class="icon">📣</div>
			<h3>Standups to your team chat</h3>
			<p>
				A daily summary of what got done, what is pending and what keeps failing, sent to Slack,
				Discord or Teams from your own machine on a schedule.
			</p>
		</div>
		<div class="feature">
			<div class="icon">👥</div>
			<h3>Team workspaces</h3>
			<p>
				Share a folder's usage with a team project. Teammates see cost and actions; prompts stay
				yours unless you share them. End-to-end encrypted workspaces too.
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
				Connect each laptop with one login; the same project counts once across agents and
				machines. See which machines are active, and revoke any of them.
			</p>
		</div>
		<div class="feature">
			<div class="icon">🧾</div>
			<h3>Provenance for audits</h3>
			<p>
				Per commit: who asked, which prompt led to it, which agent and models worked on it, and
				what it cost. Export as CSV or JSON.
			</p>
		</div>
		<div class="feature">
			<div class="icon">⌨️</div>
			<h3>Works in the terminal too</h3>
			<p>
				<code>clioilc journal</code>, <code>clioilc activity</code> and
				<code>clioilc usage report</code> show the same data locally, with or without an account.
			</p>
		</div>
	</div>
</section>

<style>
	/* Five agents fit one row on a laptop screen. */
	.agents { grid-template-columns: repeat(auto-fit, minmax(190px, 1fr)); }
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
	.agent code { background: #fff; white-space: normal; overflow-wrap: anywhere; }
</style>
