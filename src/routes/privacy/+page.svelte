<svelte:head>
	<title>Privacy Policy — clioilc</title>
</svelte:head>

<div class="page">
	<h1>Privacy Policy</h1>
	<p class="updated">Last updated: November 20, 2026</p>

	<h2>1. Information We Collect</h2>
	<p>We collect the following types of information:</p>
	<ul>
		<li>
			<strong>Account information</strong> — from GitHub when you sign in: your username, email
			address and avatar. We never see your GitHub password.
		</li>
		<li>
			<strong>Usage statistics</strong> — for each agent message and tool call: model, token
			counts, status, tool name and time, with project, session and message identifiers
			replaced by one-way hashes.
		</li>
		<li>
			<strong>Private activity data</strong> — the prompts you write, the agent's replies and
			thinking, short summaries of tool calls (such as the command run or the file path), error
			output, and project folder names. The CLI removes secrets in common formats and shortens
			long text on your machine before upload. We do not receive your source files.
		</li>
		<li>
			<strong>Device information</strong> — the name of each connected machine (its hostname,
			unless you choose another) and when it last synced. The name is shown next to the work it
			sent.
		</li>
		<li>
			<strong>Technical data</strong> — IP address and browser type in server logs, used for
			security and troubleshooting.
		</li>
		<li>
			<strong>Change history</strong> — for security, we keep a history of changes to accounts,
			devices, workspaces, projects and invitations (who changed what, and when). It does not
			include your agent activity, your email address or any keys. Entries are deleted after one
			year, and when you delete your account, your name is removed from it.
		</li>
	</ul>

	<h2>2. How We Use Your Information</h2>
	<p>We use collected information to:</p>
	<ul>
		<li>Provide, operate, and improve the Service</li>
		<li>Generate analytics and statistics on AI agent activity</li>
		<li>Detect, prevent, and address technical issues and abuse</li>
		<li>
			Email you about team workspaces, such as an invitation or an accepted invitation. We use
			your primary, verified GitHub email for this and nothing else.
		</li>
	</ul>

	<h2>3. Data Sharing</h2>
	<p>
		We do not sell your personal information. We may share data with trusted service
		providers who assist in operating the Service, or when required by law.
	</p>
	<p>
		<strong>Team workspaces.</strong> Nothing is shared with other people unless you join a
		workspace and link a folder to one of its projects with <code>clioilc link</code>. From then
		on, members who can see that project see its usage, costs, errors and tool actions (such as
		commands and file paths), with your username and the name of the device each item came
		from, from the moment you linked it, or with its earlier history if you chose that. Workspace
		admins also see the agent plans you entered on the Pricing page, compared with your usage in
		the workspace's projects. Your prompts, replies and thinking stay private unless you turn on sharing for
		that project. Workspace admins also see an audit log of membership, invitation and link
		changes. When you unlink the folder, leave the workspace or delete your account, your data
		leaves the team's view.
	</p>

	<h2>4. Data Security</h2>
	<p>
		Data is sent over HTTPS. Private activity data is encrypted at rest with a key per account.
		If you choose end-to-end encryption, it is encrypted on your machine with a key derived
		from your passphrase, and we cannot read it; if you lose the passphrase, we cannot recover
		it. Device tokens can upload data but cannot read your activity back, and you can revoke them at any
		time. No method of transmission or storage is 100% secure.
	</p>

	<h2>5. Data Retention</h2>
	<p>
		We retain your data for as long as your account is active or as needed to provide
		the Service. You can download an export of your data, or permanently delete your
		account and everything synced to it, at any time from the Account page of the
		dashboard; you can also <a href="/contact">contact us</a> to do it for you. Data kept locally by the CLI (in
		<code>~/.clioilc</code>) stays on your machine and is yours to delete.
	</p>

	<h2>6. Your Rights</h2>
	<p>Depending on your jurisdiction, you may have the right to:</p>
	<ul>
		<li>Access, correct, or delete your personal data</li>
		<li>Export your data in a portable format</li>
		<li>Object to or restrict certain processing</li>
	</ul>

	<h2>7. Contact</h2>
	<p>Questions about this policy? <a href="/contact">Contact us</a>.</p>
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
