<script lang="ts">
	import type INavLink from '../util/INavLink';

	let menuState: string = 'closed';

	// props
	export let navLinks: INavLink[];
</script>

<div class="navbar-container" />

<!-- This is the mobile navbar for smaller devices -->
<div class={menuState === 'open' ? 'mobile-navbar closed' : 'mobile-navbar opened'}>
	<i on:click={() => (menuState = 'open')} class="bi bi-list" />
</div>

<div class={menuState === 'open' ? 'navbar-content visible' : 'navbar-content closed'}>
	<i on:click={() => (menuState = 'closed')} class="bi bi-x-circle-fill" />
	<ul>
		{#each navLinks as link}
			<li href={link.link} class="navbar-link">{link.displayText}</li>
		{/each}
	</ul>
</div>

<style>
	.navbar-container {
		height: 100vh;
		width: 100px;
		background-color: #252526;
		display: none;
	}

	.mobile-navbar {
		display: flex;
		justify-content: flex-end;
		background-color: #252526;
		color: white;
		width: 100%;
		padding: 1rem;
	}

	.mobile-navbar i {
		display: flex;
		font-size: 1.5rem;
		color: white;
		cursor: pointer;
		transition: background-color 400ms ease;
	}

	.mobile-navbar i:hover {
		background: linear-gradient(
			to right,
			rgba(255, 0, 0, 1),
			rgba(255, 0, 180, 1),
			rgba(0, 100, 200, 1)
		);
		background-clip: inherit;
		-webkit-background-clip: text;
		-webkit-text-fill-color: transparent;
		-moz-background-clip: text;
		-moz-text-fill-color: transparent;
	}

	.mobile-navbar.opened {
		display: flex;
	}

	.mobile-navbar.closed {
		display: none;
	}

	.closed {
		display: none;
	}

	.navbar-content {
		display: flex;
		justify-content: center;
		visibility: hidden;
		align-items: center;
		flex-direction: column;
		background-color: #252526;
		width: 100%;
		height: 0;
		transition: all 400ms linear;
	}

	.navbar-content i {
		color: white;
		font-size: 2.5rem;
		transition: background-color 400ms ease;
		margin-bottom: 2rem;
	}

	.navbar-content i:hover {
		background: linear-gradient(
			to right,
			rgba(255, 0, 0, 1),
			rgba(255, 0, 180, 1),
			rgba(0, 100, 200, 1)
		);
		background-clip: inherit;
		-webkit-background-clip: text;
		-webkit-text-fill-color: transparent;
		-moz-background-clip: text;
		-moz-text-fill-color: transparent;
		cursor: pointer;
	}

	.navbar-content.visible {
		visibility: visible;
		height: 100vh;
	}

	ul {
		justify-content: center;
		list-style-type: none;
		margin: 0;
		padding: 0;
		text-align: center;
	}

	li:not(:last-child) {
		margin-bottom: 1rem;
	}

	.navbar-link {
		color: white;
		font-size: 18pt;
		background: linear-gradient(to right, transparent, transparent),
			linear-gradient(to right, rgba(255, 0, 0, 1), rgba(255, 0, 180, 1), rgba(0, 100, 200, 1));
		background-size: 100% 0.1em, 0 0.1em;
		background-position: 100% 100%, 0 100%;
		background-repeat: no-repeat;
		transition: background-size 400ms ease;
	}
	.navbar-link:hover,
	.navbar-link:focus {
		cursor: pointer;
		background-size: 0 0.1em, 100% 0.1em;
	}
</style>
