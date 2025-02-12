<script lang="ts">
	let email = '';
	let notification = '';

	async function handleForgotPassword() {
		const formData = new FormData();
		formData.append('email', email);

		const response = await fetch('/login/forgot-password', {
			method: 'POST',
			body: formData,
		});

		if (response.ok) {
			notification = 'A link to reset your password has been sent to your email. Redirecting to login...';
		} else {
			notification = 'Failed to send the password reset link. Please try again.';
		}
	}
</script>

<div class="page-container">
	<img src="/login-back.png" class="background" alt="">
	<form class="forgot-password-form" on:submit|preventDefault={handleForgotPassword}>
		<h1>Forgot Password?</h1>

		<label for="email">Email Address</label>
		<input id="email" type="email" bind:value={email} placeholder="Enter your email" required />

		<button type="submit"><strong>Send</strong></button>

		<div class="links">
			<a href="/login">Back to Login</a>
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

	.forgot-password-form {
		background-color: #fff;
		padding: 30px;
		border-radius: 10px;
		box-shadow: 0 4px 10px rgba(0, 0, 0, 0.2);
		width: 700px;
		text-align: center;
		position: absolute;
	}

	.forgot-password-form h1 {
		font-size: 2em;
		color: #007bff;
		margin-bottom: 20px;
	}

	.forgot-password-form label {
		display: block;
		margin-bottom: 10px;
		font-size: 1.1em;
		color: #555;
		text-align: left;
	}

	.forgot-password-form input[type="email"] {
		width: 100%;
		padding: 10px;
		margin-bottom: 15px;
		border: 1px solid #ddd;
		border-radius: 5px;
		font-size: 1em;
	}

	.forgot-password-form button {
		background-color: #007bff;
		color: white;
		padding: 12px;
		border: none;
		border-radius: 5px;
		font-size: 1.2em;
		width: 100%;
		cursor: pointer;
	}

	.forgot-password-form button:hover {
		background-color: #0056b3;
	}

	.links {
		margin-top: 15px;
		display: flex;
		justify-content: center;
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
