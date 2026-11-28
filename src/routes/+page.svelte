<script>
	import { DASH_URL, TRACKER_REPO } from '$lib/site.js';

	const dash = DASH_URL.replace('https://', '');

	// Real dashboard screenshots (static/screens), cropped so no prompts,
	// paths or project names show.
	const tour = [
		{
			src: '/screens/compare.webp',
			path: '/compare',
			w: 1247,
			h: 640,
			label: 'Compare',
			title: 'Which agent is worth it',
			text: 'Claude Code next to Devin, model by model, over the same work: what each one cost, how much of it shipped, and the price per delivered item and per commit.',
			alt: 'Compare page: agents and models side by side with responses, cost, items delivered, commits and cost per commit'
		},
		{
			src: '/screens/pricing.webp',
			path: '/pricing',
			w: 1247,
			h: 528,
			label: 'Plans',
			title: 'Does your plan pay off?',
			text: 'Your month so far at API rates, projected to the end of the month, against the plan you pay for, and which plan would cost less for the way you actually work.',
			alt: 'Plans page: month-to-date API-equivalent cost per agent, projected month-end cost, and a plan that would cost less'
		},
		{
			src: '/screens/report.webp',
			path: '/report',
			w: 920,
			h: 218,
			label: 'Reports',
			title: 'A report your client can read',
			text: 'Work items, delivery, commits, active time and AI cost for a project and period. Print it, save it as PDF or export CSV. Prompts are never in it.',
			alt: 'Work report summary: work items, delivered, commits, pull requests, active time, AI responses, tokens and AI cost'
		}
	];
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
		<a class="btn btn-ghost" href="#tour">See the dashboard</a>
	</div>
	<figure class="shot hero-shot">
		<div class="shot-bar" aria-hidden="true">
			<span></span><span></span><span></span>
			<em>{dash}</em>
		</div>
		<img
			src="/screens/overview.webp"
			width="1247"
			height="654"
			fetchpriority="high"
			alt="clioilc overview: a year of succeeded and failed tool calls per day, and cost, messages, tokens and tool calls for the last 7 days"
		/>
	</figure>
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

<section id="tour">
	<p class="section-label">A Look Inside</p>
	<h2>Answers, not just logs</h2>
	<p class="section-sub">
		Real screens from the dashboard. Every number comes from your agents' own history.
	</p>
	{#each tour as t, i}
		<div class="tour-row" class:flip={i % 2 === 1}>
			<div class="tour-text">
				<p class="tour-label">{t.label}</p>
				<h3>{t.title}</h3>
				<p>{t.text}</p>
			</div>
			<figure class="shot">
				<div class="shot-bar" aria-hidden="true">
					<span></span><span></span><span></span>
					<em>{dash}{t.path}</em>
				</div>
				<img src={t.src} width={t.w} height={t.h} loading="lazy" alt={t.alt} />
			</figure>
		</div>
	{/each}
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

	/* Screenshots in a light browser frame. */
	.shot {
		border: 1px solid var(--border);
		border-radius: 14px;
		overflow: hidden;
		background: #fafafa;
		box-shadow:
			0 1px 2px rgba(0, 0, 0, 0.04),
			0 24px 60px -20px rgba(0, 0, 0, 0.18);
	}
	.shot img { display: block; width: 100%; height: auto; }
	.shot-bar {
		display: flex;
		align-items: center;
		gap: 6px;
		padding: 0.6rem 0.9rem;
		border-bottom: 1px solid var(--border);
		background: #f3f3f3;
	}
	.shot-bar span { width: 10px; height: 10px; border-radius: 50%; background: #d9d9d9; }
	.shot-bar em {
		margin-left: 0.75rem;
		font-style: normal;
		font-size: 0.72rem;
		color: var(--muted);
		font-family: 'SF Mono', Menlo, Consolas, monospace;
		white-space: nowrap;
		overflow: hidden;
		text-overflow: ellipsis;
	}
	.hero-shot {
		position: relative;
		z-index: 1;
		width: min(1100px, 100%);
		margin-top: 4.5rem;
		text-align: left;
	}

	.tour-row {
		display: grid;
		grid-template-columns: minmax(0, 1fr) minmax(0, 1.9fr);
		gap: 3rem;
		align-items: center;
		margin-bottom: 5rem;
	}
	.tour-row:last-child { margin-bottom: 0; }
	/* Flipped: the screenshot keeps the wide column, now on the left. */
	.tour-row.flip { grid-template-columns: minmax(0, 1.9fr) minmax(0, 1fr); }
	.tour-row.flip .tour-text { order: 2; }
	.tour-label {
		font-size: 0.72rem;
		letter-spacing: 0.18em;
		text-transform: uppercase;
		color: var(--muted);
		margin-bottom: 0.6rem;
	}
	.tour-text h3 { font-size: 1.5rem; letter-spacing: -0.01em; margin-bottom: 0.75rem; }
	.tour-text p:last-child { color: var(--muted); font-size: 0.95rem; }
	@media (max-width: 820px) {
		.tour-row,
		.tour-row.flip { grid-template-columns: 1fr; gap: 1.5rem; margin-bottom: 3.5rem; }
		.tour-row.flip .tour-text { order: 0; }
		.hero-shot { margin-top: 3rem; }
	}
</style>
