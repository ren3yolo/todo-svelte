<script>
	// @ts-nocheck

	import { onMount } from 'svelte';
	import '../app.css';
	import { createClient, loginWithPopup } from '../authService';
	import { isAuthenticated, user, loading } from '../store';
	import Login from './components/Login.svelte';
	import Navbar from './components/Navbar.svelte';
	import Spinner from './components/Spinner.svelte';

	/**
	 * @type {import("@auth0/auth0-spa-js").Auth0Client}
	 */
	let auth0Client;

	onMount(async () => {
		auth0Client = await createClient();
		auth0Client.isAuthenticated().then((data) => {
			loading.set(false);
			isAuthenticated.set(data);
		});
		user.set(await auth0Client.getUser());
	});

	function login() {
		loginWithPopup(auth0Client);
	}
</script>

<Navbar />
{#if $loading}
	<Spinner loading />
{:else if !$isAuthenticated}
	<Login on:login={login} />
{:else}
	<slot />
{/if}
