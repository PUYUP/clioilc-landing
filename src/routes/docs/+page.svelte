<script>
	import Code from '$lib/Code.svelte';
	import { API_URL, DASH_URL, TRACKER_REPO } from '$lib/site.js';

	const toc = [
		{ id: 'how-it-works', label: 'How it works' },
		{ id: 'requirements', label: 'Requirements' },
		{ id: 'install', label: '1. Install the CLI' },
		{ id: 'try-locally', label: '2. Try it locally' },
		{ id: 'connect', label: '3. Connect to your account' },
		{ id: 'sync', label: '4. Upload your history' },
		{ id: 'background', label: '5. Keep it running' },
		{ id: 'dashboard', label: '6. Use the dashboard' },
		{ id: 'more-machines', label: 'More machines' },
		{ id: 'privacy', label: 'Privacy & encryption' },
		{ id: 'troubleshooting', label: 'Troubleshooting' },
		{ id: 'uninstall', label: 'Uninstall' },
		{ id: 'reference', label: 'Command reference' }
	];
</script>

<svelte:head>
	<title>Docs — clioilc</title>
	<meta
		name="description"
		content="Install clioilc, connect it to your dashboard, and see what your AI coding agents did, step by step."
	/>
</svelte:head>

<div class="docs">
	<aside>
		<nav aria-label="On this page">
			<p class="toc-title">On this page</p>
			<ol>
				{#each toc as t (t.id)}<li><a href={`#${t.id}`}>{t.label}</a></li>{/each}
			</ol>
		</nav>
	</aside>

	<article>
		<p class="eyebrow">Documentation</p>
		<h1>Getting started</h1>
		<p class="lead">
			From installing the CLI to reading your agent's day in the dashboard. Takes about ten
			minutes.
		</p>

		<h2 id="how-it-works">How it works</h2>
		<p>clioilc has two parts:</p>
		<ul>
			<li>
				<strong>The <code>clioilc</code> CLI</strong> runs on the machine where you use your AI
				agent. It reads the agent's local session logs, keeps a copy in
				<code>~/.clioilc/usage.db</code>, and uploads new rows to your account.
			</li>
			<li>
				<strong>The dashboard</strong> at <a href={DASH_URL}>{DASH_URL.replace('https://', '')}</a> shows
				cost, tokens, errors and a timeline of every prompt, reply and tool call.
			</li>
		</ul>
		<p>
			Everything works locally first: you can inspect your usage in the terminal before you
			connect an account, and nothing leaves your machine until you run <code>clioilc login</code>.
		</p>
		<div class="note">
			<strong>Supported agents today:</strong> Claude Code. Readers for other agents are on the
			way.
		</div>

		<h2 id="requirements">Requirements</h2>
		<ul>
			<li><strong>macOS or Linux.</strong> (The background service needs launchd or systemd.)</li>
			<li>
				<strong>Claude Code</strong>, used at least once on this machine, so that session logs
				exist in <code>~/.claude/projects</code>.
			</li>
			<li>
				<strong>Rust 1.89 or newer</strong> to build the CLI. Install it from
				<a href="https://rustup.rs">rustup.rs</a> if <code>cargo --version</code> doesn't work.
			</li>
			<li><strong>A GitHub account</strong> to sign in to the dashboard.</li>
		</ul>

		<h2 id="install">1. Install the CLI</h2>
		<p>Build and install the latest version from GitHub:</p>
		<Code code={`cargo install --git ${TRACKER_REPO} clioilc --locked`} />
		<p>
			This puts <code>clioilc</code> in <code>~/.cargo/bin</code>, which rustup adds to your
			<code>PATH</code>. Check that it works:
		</p>
		<Code code="clioilc --help" />
		<p class="small">
			To update later, run the same <code>cargo install</code> command again with
			<code>--force</code>.
		</p>

		<h2 id="try-locally">2. Try it locally</h2>
		<p>
			Read your existing Claude Code history into <code>~/.clioilc/usage.db</code>. It's safe to
			run again: records are never counted twice.
		</p>
		<Code code="clioilc usage import" />
		<p>Then look at it:</p>
		<Code
			code={`# tokens and errors per day (or --by model / --by project)
clioilc usage report --by day

# what the agent did today: prompts, replies and tool calls
clioilc activity

# another day, with the agent's thinking and full text
clioilc activity --date 2026-11-14 --thinking --full`}
		/>
		<p>
			Nothing is uploaded yet. Prompts, replies and tool details are stored on this machine with
			secrets (API keys, tokens, passwords in common formats) redacted.
		</p>

		<h2 id="connect">3. Connect to your account</h2>
		<Code code={`clioilc login --server ${API_URL}`} />
		<p>The CLI prints a code and opens your browser:</p>
		<Code
			label="Output"
			code={`  Open:  ${DASH_URL}/device
  Code:  ABCD-EFGH

waiting for approval (Ctrl+C to cancel) ...`}
		/>
		<ol class="steps">
			<li>Sign in with GitHub in the browser.</li>
			<li>
				Check that the device name and the code match what your terminal shows, then click
				<strong>Allow</strong>. Only allow codes you just requested yourself.
			</li>
			<li>Go back to the terminal. The login finishes on its own.</li>
		</ol>
		<p>
			The first time you log in, the CLI asks how your <strong>private data</strong> (prompts,
			replies, thinking, tool details, project names) should be stored. You can't change this
			later.
		</p>
		<table>
			<thead>
				<tr><th></th><th>Server-side encryption</th><th>End-to-end encryption</th></tr>
			</thead>
			<tbody>
				<tr><th>Who encrypts</th><td>The server, at rest</td><td>Your machine, before upload</td></tr>
				<tr><th>Can the server read it?</th><td>Yes</td><td>No</td></tr>
				<tr><th>Lost passphrase or laptop</th><td>Nothing lost</td><td>Private data is unrecoverable</td></tr>
				<tr><th>In the dashboard</th><td>Just sign in</td><td>Enter your passphrase to unlock</td></tr>
			</tbody>
		</table>
		<p>
			Choose at the prompt, or pass it up front with <code>--mode server</code> or
			<code>--mode e2e</code>. End-to-end asks for a passphrase of at least 12 characters; keep it
			somewhere safe.
		</p>
		<p class="small">
			Options: <code>--name "Work laptop"</code> sets the device name shown in the dashboard
			(default: the hostname). <code>--no-browser</code> skips opening the browser.
		</p>

		<h2 id="sync">4. Upload your history</h2>
		<Code code="clioilc sync" />
		<Code label="Output" code={`synced 2385 message(s), 2568 tool call(s), 4154 private row(s) to ${API_URL}`} />
		<p>
			Uploads go in batches and can be repeated safely. If the network drops, the next
			<code>sync</code> sends whatever didn't make it.
		</p>

		<h2 id="background">5. Keep it running</h2>
		<p>Install the background service so new activity is recorded and uploaded automatically:</p>
		<Code code={`clioilc service install
clioilc service status`} />
		<p>
			The service runs <code>clioilc watch --sync</code> at every login and restarts it if it
			stops. New activity reaches the dashboard within about 30 seconds. It uses a LaunchAgent
			on macOS and a <code>systemd --user</code> unit on Linux, and logs to
			<code>~/.clioilc/watch.log</code>.
		</p>
		<Code
			code={`# what it's doing, plus the last log lines
clioilc service status

# stop and remove it
clioilc service uninstall`}
		/>
		<p class="small">
			Prefer a terminal window? <code>clioilc watch --sync</code> does the same in the
			foreground; stop it with Ctrl+C. Don't run both at once.
		</p>

		<h2 id="dashboard">6. Use the dashboard</h2>
		<p>Open <a href={DASH_URL}>{DASH_URL.replace('https://', '')}</a> and sign in with GitHub.</p>
		<h3>Overview</h3>
		<ul>
			<li>
				<strong>Calendar</strong> of the last 12 months: tool calls that succeeded and failed per
				day. Click a day to open its activity; a click in the failed row opens just the errors.
			</li>
			<li>
				<strong>Cost</strong>, messages, tokens and tool calls for the last 24 hours, 7, 30 or 90
				days, hourly or daily. Click a column to open that day.
			</li>
			<li><strong>Cost by project and by model</strong>, to see where the spend goes.</li>
		</ul>
		<div class="note">
			Cost is the <strong>Claude API price</strong> of your tokens, not your bill. If you use
			Claude Code through a subscription, it shows what the same work would cost on the API.
		</div>
		<h3>Activity</h3>
		<ul>
			<li>One day at a time, newest first, grouped by session, with the cost of each session.</li>
			<li>
				Filter by type (<strong>You</strong>, <strong>Agent</strong>, <strong>Thinking</strong>,
				<strong>Tool</strong>) and status (<strong>Succeeded</strong>, <strong>Error</strong>),
				by project, or search the text.
			</li>
			<li>
				With end-to-end encryption, enter your passphrase once per tab. Decryption happens in
				your browser.
			</li>
		</ul>
		<h3>Devices</h3>
		<p>
			Every connected machine, whether it synced in the last 5 minutes, and how much it sent.
			<strong>Revoke</strong> stops a machine from uploading right away; data it already sent
			stays.
		</p>

		<h2 id="more-machines">More machines</h2>
		<p>Repeat steps 1, 3, 4 and 5 on each machine. Its data joins the same dashboard.</p>
		<p>
			If that machine already has a local <code>usage.db</code>, the login moves it aside
			(<code>usage.db.before-login-…</code>) and rebuilds it from the agent logs, so that the same
			project counts as one project across machines. Stop any running <code>clioilc watch</code>
			on it first. History whose logs were already deleted stays only in that backup.
		</p>

		<h2 id="privacy">Privacy & encryption</h2>
		<ul>
			<li>
				<strong>Statistics</strong> (model, token counts, status, tool names, time) are stored
				with hashed ids: no file paths, project names, branches or text.
			</li>
			<li>
				<strong>Private data</strong> (prompts, replies, thinking, tool summaries, error output,
				project names) is encrypted at rest, server-side or end-to-end as you chose, and only
				ever shown to you.
			</li>
			<li>
				<strong>Secrets</strong> in common formats are redacted on your machine before anything
				is stored, and long text is cut to a maximum length.
			</li>
			<li>
				<strong>Your device token</strong> lives in <code>~/.clioilc/auth.json</code>, readable
				only by you. It can upload data, but it can't read your activity or statistics back.
			</li>
		</ul>

		<h2 id="troubleshooting">Troubleshooting</h2>
		<dl>
			<dt><code>not logged in; run `clioilc login --server &lt;url&gt;` first</code></dt>
			<dd>Run step 3. The background service also needs a login before it can be installed.</dd>

			<dt><code>this device was revoked or logged out; run `clioilc login`</code></dt>
			<dd>The device was revoked in the dashboard. Log in again to reconnect it.</dd>

			<dt><code>usage.db was hashed with a different salt than your account</code></dt>
			<dd>
				The local database doesn't belong to this account (for example, a copy from another
				machine). Run <code>clioilc login</code> again; it rebuilds the database for you.
			</dd>

			<dt><code>wrong passphrase</code></dt>
			<dd>
				The end-to-end passphrase didn't unlock your keys. Passphrases can't be reset; try the
				exact one you chose on your first login.
			</dd>

			<dt><code>another `clioilc sync` is running</code></dt>
			<dd>The background service is already syncing. Nothing to do.</dd>

			<dt>Nothing new shows up in the dashboard</dt>
			<dd>
				Run <code>clioilc service status</code>. If it isn't running, run
				<code>clioilc service install</code> again; the last log lines usually say why it stopped.
				A manual <code>clioilc sync</code> also reports any error directly.
			</dd>
		</dl>

		<h2 id="uninstall">Uninstall</h2>
		<Code
			code={`# stop the background service
clioilc service uninstall

# revoke this machine and remove its login (local data is kept)
clioilc logout

# remove local data and the CLI
rm -r ~/.clioilc
cargo uninstall clioilc`}
		/>

		<h2 id="reference">Command reference</h2>
		<table class="ref">
			<tbody>
				<tr><td><code>clioilc usage import</code></td><td>Read existing agent logs into the local database</td></tr>
				<tr><td><code>clioilc usage report --by day|model|project</code></td><td>Token and error totals in the terminal</td></tr>
				<tr><td><code>clioilc activity [--date] [--project] [--thinking] [--full]</code></td><td>What the agent did on a day</td></tr>
				<tr><td><code>clioilc login --server &lt;url&gt; [--mode server|e2e] [--name]</code></td><td>Connect this machine to your account</td></tr>
				<tr><td><code>clioilc sync</code></td><td>Upload everything not yet on the server</td></tr>
				<tr><td><code>clioilc watch --sync</code></td><td>Record new activity and upload it every 30 s (foreground)</td></tr>
				<tr><td><code>clioilc service install|status|uninstall</code></td><td>Run <code>watch --sync</code> in the background at login</td></tr>
				<tr><td><code>clioilc logout</code></td><td>Revoke this machine and forget the login</td></tr>
			</tbody>
		</table>
		<p class="small">
			Every command accepts <code>--data-dir &lt;dir&gt;</code> (default <code>~/.clioilc</code>)
			and <code>--help</code>. Source and full CLI documentation:
			<a href={TRACKER_REPO}>{TRACKER_REPO.replace('https://', '')}</a>.
		</p>
	</article>
</div>

<style>
	.docs {
		max-width: 1100px;
		margin: 0 auto;
		padding: 7rem 2rem 5rem;
		display: grid;
		grid-template-columns: 210px minmax(0, 1fr);
		gap: 3.5rem;
	}
	aside nav { position: sticky; top: 2rem; }
	.toc-title {
		font-size: 0.7rem;
		letter-spacing: 0.15em;
		text-transform: uppercase;
		color: var(--muted);
		margin-bottom: 0.75rem;
	}
	aside ol { list-style: none; display: grid; gap: 0.35rem; }
	aside a { color: var(--muted); text-decoration: none; font-size: 0.85rem; }
	aside a:hover { color: var(--fg); }
	article { min-width: 0; max-width: 720px; }
	.eyebrow {
		font-size: 0.75rem;
		letter-spacing: 0.2em;
		text-transform: uppercase;
		color: var(--muted);
		margin-bottom: 0.75rem;
	}
	h1 { font-size: clamp(2rem, 5vw, 3rem); font-weight: 600; letter-spacing: -0.02em; margin-bottom: 0.75rem; }
	.lead { font-size: 1.1rem; color: var(--muted); margin-bottom: 1rem; }
	h2 {
		font-size: 1.45rem;
		letter-spacing: -0.01em;
		margin: 3.25rem 0 0.75rem;
		scroll-margin-top: 1.5rem;
	}
	h3 { font-size: 1.05rem; margin: 1.75rem 0 0.5rem; }
	p, li, dd, td { color: #444; font-size: 0.95rem; }
	p { margin-bottom: 0.75rem; }
	ul, ol.steps { padding-left: 1.25rem; margin-bottom: 1rem; }
	li { margin-bottom: 0.4rem; }
	a { color: var(--fg); }
	strong { color: var(--fg); }
	code {
		font-family: "SF Mono", Menlo, Consolas, monospace;
		font-size: 0.85em;
		background: var(--card);
		border: 1px solid var(--border);
		border-radius: 6px;
		padding: 0.05rem 0.35rem;
		overflow-wrap: anywhere;
	}
	.small { font-size: 0.85rem; color: var(--muted); }
	.note {
		border: 1px solid var(--border);
		background: var(--card);
		border-radius: 12px;
		padding: 0.9rem 1.1rem;
		margin: 1rem 0 1.25rem;
		font-size: 0.9rem;
		color: #444;
	}
	table { width: 100%; border-collapse: collapse; margin: 1rem 0 1.25rem; font-size: 0.9rem; display: block; overflow-x: auto; }
	th, td { text-align: left; padding: 0.6rem 0.75rem; border-bottom: 1px solid var(--border); vertical-align: top; }
	thead th { font-size: 0.75rem; letter-spacing: 0.08em; text-transform: uppercase; color: var(--muted); }
	tbody th { font-weight: 600; color: var(--fg); white-space: nowrap; }
	.ref td:first-child { white-space: nowrap; }
	dl { margin: 1rem 0; }
	dt { margin-top: 1.1rem; font-weight: 600; font-size: 0.92rem; }
	dd { margin: 0.35rem 0 0; }
	@media (max-width: 860px) {
		.docs { grid-template-columns: 1fr; gap: 1.5rem; padding-top: 6rem; }
		aside nav { position: static; border: 1px solid var(--border); border-radius: 12px; padding: 1rem 1.25rem; }
		aside ol { grid-template-columns: repeat(2, minmax(0, 1fr)); column-gap: 1rem; row-gap: 0.2rem; }
		aside a { font-size: 0.8rem; }
		.ref td:first-child { white-space: normal; }
	}
</style>
