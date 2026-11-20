<script>
	// A shell snippet with a copy button. Lines starting with "#" are
	// comments and are not copied.
	/** @type {{ code: string, label?: string }} */
	let { code, label = 'Terminal' } = $props();
	let copied = $state(false);

	async function copy() {
		const text = code
			.split('\n')
			.filter((l) => !l.trimStart().startsWith('#'))
			.join('\n')
			.trim();
		try {
			await navigator.clipboard.writeText(text);
			copied = true;
			setTimeout(() => (copied = false), 1500);
		} catch {
			/* clipboard blocked: the text is still selectable */
		}
	}
</script>

<div class="code">
	<div class="bar">
		<span>{label}</span>
		<button type="button" onclick={copy} aria-label="Copy commands">{copied ? 'Copied' : 'Copy'}</button>
	</div>
	<pre><code>{code}</code></pre>
</div>

<style>
	.code {
		border: 1px solid var(--border);
		border-radius: 12px;
		margin: 1rem 0 1.25rem;
		overflow: hidden;
		background: #fbfbfb;
	}
	.bar {
		display: flex;
		justify-content: space-between;
		align-items: center;
		padding: 0.4rem 0.75rem 0.4rem 1rem;
		border-bottom: 1px solid var(--border);
		font-size: 0.7rem;
		letter-spacing: 0.12em;
		text-transform: uppercase;
		color: var(--muted);
	}
	button {
		border: 1px solid var(--border);
		background: #fff;
		border-radius: 999px;
		padding: 0.2rem 0.75rem;
		font: inherit;
		font-size: 0.7rem;
		letter-spacing: 0.08em;
		cursor: pointer;
		color: var(--fg);
	}
	button:hover { border-color: var(--muted); }
	pre {
		margin: 0;
		padding: 1rem;
		overflow-x: auto;
		font-family: "SF Mono", Menlo, Consolas, monospace;
		font-size: 0.82rem;
		line-height: 1.6;
		color: var(--fg);
	}
</style>
