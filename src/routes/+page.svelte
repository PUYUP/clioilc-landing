<svelte:head>
	<title>clioilc — AI Agent Interaction Tracker</title>
	<meta
		name="description"
		content="Track every AI agent interaction — Claude, Gemini, Codex, and more — in a single dashboard."
	/>
</svelte:head>

<header class="hero">
	<span class="badge">Observability for AI Agents</span>
	<h1 class="logo">clioilc</h1>
	<p class="tagline">
		Track every AI agent interaction — Claude, Gemini, Codex, and more — in a single dashboard.
		Monitor errors, refactors, improvisations, and all agent activity across your codebase.
	</p>
	<div class="cta">
		<a class="btn btn-primary" href="/docs">Start Tracking</a>
		<a class="btn btn-ghost" href="#stats">View Stats</a>
	</div>
</header>

<section id="agents">
	<p class="section-label">Supported Agents</p>
	<h2>Every coding agent, one place</h2>
	<p class="section-sub">
		clioilc integrates with the most popular AI coding agents and automatically records
		every interaction, tool call, and code change.
	</p>
	<div class="agents">
		<div class="agent"><h3><span class="dot" style="background:#d97757"></span>Claude</h3><p>Track Claude Code, Claude.ai, and API interactions.</p></div>
		<div class="agent"><h3><span class="dot" style="background:#4285f4"></span>Gemini</h3><p>Monitor Gemini CLI and Google AI agent sessions.</p></div>
		<div class="agent"><h3><span class="dot" style="background:#10a37f"></span>Codex</h3><p>Analyze OpenAI Codex work across your codebase.</p></div>
		<div class="agent"><h3><span class="dot" style="background:#999999"></span>And more</h3><p>GPT, Copilot, Aider, Devin, and custom agents.</p></div>
	</div>
</section>

<section id="stats">
	<p class="section-label">Stats Dashboard</p>
	<h2>Data, not guesses</h2>
	<p class="section-sub">
		Get clear insights into your agents' performance and behavior across every project.
	</p>
	<div class="stats">
		<div class="stat"><div class="value">1.2%</div><div class="label">Error Rate</div></div>
		<div class="stat"><div class="value">1,847</div><div class="label">Files Refactored</div></div>
		<div class="stat"><div class="value">326</div><div class="label">Improvisations</div></div>
		<div class="stat"><div class="value">48.2M</div><div class="label">Tokens Used</div></div>
		<div class="stat"><div class="value">12,904</div><div class="label">Sessions Tracked</div></div>
		<div class="stat"><div class="value">3.4m</div><div class="label">Avg. Resolution</div></div>
	</div>
</section>

<section id="how-it-works">
	<p class="section-label">How It Works</p>
	<h2>Three steps to full visibility</h2>
	<p class="section-sub">
		No complex setup. clioilc works with the tools you already use.
	</p>
	<div class="steps">
		<div class="step">
			<div class="step-number">1</div>
			<h3>Install the CLI</h3>
			<p>Install <code>clioilc</code> globally in seconds. No agents to wrap, no proxies to configure, and no changes to how you already work.</p>
		</div>
		<div class="step">
			<div class="step-number">2</div>
			<h3>Auto-Scan Project JSONs</h3>
			<p>Run <code>clioilc</code> in your project root. It automatically discovers and parses local agent session and log <code>.json</code> files (Claude, Gemini, Codex, and more).</p>
		</div>
		<div class="step">
			<div class="step-number">3</div>
			<h3>Get Instant Insights</h3>
			<p>See clear terminal stats on tool calls, error loops, unexpected file edits, and side-by-side agent performance — all locally on your machine.</p>
		</div>
	</div>
</section>

<section id="features">
	<p class="section-label">Features</p>
	<h2>What you can track</h2>
	<p class="section-sub">
		From error detection to agent improvisation patterns — everything is logged and analyzable.
	</p>
	<div class="features">
		<div class="feature">
			<div class="icon">⚠️</div>
			<h3>Error Tracking</h3>
			<p>Detect errors produced by agents — syntax errors, build failures, and runtime issues — with breakdowns per agent and per file.</p>
		</div>
		<div class="feature">
			<div class="icon">♻️</div>
			<h3>Refactor Metrics</h3>
			<p>Measure how often and how extensively agents refactor code, including complexity changes.</p>
		</div>
		<div class="feature">
			<div class="icon">✨</div>
			<h3>Improvisation</h3>
			<p>Track when agents take initiative on their own — problem solving, optimizations, and decisions beyond the original prompt.</p>
		</div>
		<div class="feature">
			<div class="icon">📊</div>
			<h3>Agent Comparison</h3>
			<p>Compare Claude vs Gemini vs Codex performance based on accuracy, speed, and error rates.</p>
		</div>
		<div class="feature">
			<div class="icon">⏱️</div>
			<h3>Session Timeline</h3>
			<p>Replay every agent session chronologically — prompts, actions, tool calls, and results.</p>
		</div>
		<div class="feature">
			<div class="icon">🔔</div>
			<h3>Alerts &amp; Export</h3>
			<p>Get notified when error rates spike, and export data to CSV/JSON for deeper analysis.</p>
		</div>
	</div>
</section>
