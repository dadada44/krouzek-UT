<script>
	import { goto } from '$app/navigation';

	let loginSuccess = false;
	let notification = '';
	let nickname = '';
	let password = '';
	let rememberMe = false;

	async function login(event) {
		event.preventDefault();
		notification = '';

		const formData = new FormData();
		formData.append('nickname', nickname);
		formData.append('password', password);
		formData.append('rememberMe', rememberMe ? 'true' : 'false');

		try {
			const response = await fetch('/login', {
				method: 'POST',
				body: formData,
			});

			const result = await response.json();

			if (response.ok) {
				if (result.success) {
					loginSuccess = true;
					setTimeout(() => {
						goto('/profile');
					}, 1000);
				} else {
					notification = result.message;
				}
			} else {
				notification = result.message || 'An unexpected error occurred. Please try again later.';
			}
		} catch (error) {
			notification = 'An unexpected error occurred. Please try again later.';
			console.error(error);
		}
	}
</script>

<div class="page-container">
	<img src="/login-back.png" class="background" alt="">
	<form class="login-form" on:submit={login}>
		<h1>LOGIN</h1>
		<label>
			Nick
			<input type="text" bind:value={nickname} required />
		</label>
		<label>
			Heslo
			<input type="password" bind:value={password} required />
		</label>
		<div class="remember-me">
			<input type="checkbox" bind:checked={rememberMe} />
			<span>Remember me</span>
		</div>
		<button type="submit"><strong>Přihlásit se</strong></button>
		<div class="links">
			<a href="/register">Nová registrace</a>
			<a href="/forgot-password">Zapomenuté heslo</a>
		</div>
	</form>

	{#if notification}
		<p class="notification">{notification}</p>
	{/if}
</div>

<style>
	.background{
		width: 100vw;
		position: absolute;
		object-fit: cover;
		z-index: -1;
		top: 0;
		height: 100%;
		filter: brightness(0.9);
	}


	.page-container {
		display: flex;
		flex-direction: column;
		align-items: center;
		position: relative;
		min-height: 100vh;
		justify-content: center;
	}

	.login-form {
		background-color: #fff;
		padding: 30px;
		border-radius: 10px;
		box-shadow: 0 4px 10px rgba(0, 0, 0, 0.2);
		width: 400px;
		text-align: center;
	}

	.login-form h1 {
		font-size: 2em;
		color: #007bff;
		margin-bottom: 20px;
	}

	.login-form label {
		display: block;
		margin-bottom: 10px;
		font-size: 1.1em;
		color: #555;
		text-align: left;
	}

	.login-form input[type="text"],
	.login-form input[type="password"] {
		width: 100%;
		padding: 10px;
		margin-bottom: 15px;
		border: 1px solid #ddd;
		border-radius: 5px;
		font-size: 1em;
	}

	.remember-me {
		display: flex;
		align-items: center;
		margin-bottom: 15px;
		font-size: 0.9em;
		color: #555;
	}

	.remember-me input {
		margin-right: 5px;
	}

	.login-form button {
		background-color: #007bff;
		color: white;
		padding: 12px;
		border: none;
		border-radius: 5px;
		font-size: 1.2em;
		width: 100%;
		cursor: pointer;
	}

	.login-form button:hover {
		background-color: #0056b3;
	}

	.links {
		margin-top: 15px;
		display: flex;
		justify-content: space-between;
		font-size: 0.9em;
	}

	.links a {
		color: #007bff;
		text-decoration: none;
	}

	.links a:hover {
		text-decoration: underline;
	}

	.notification {
		margin-top: 20px;
		color: red;
		font-size: 1em;
	}
</style>
