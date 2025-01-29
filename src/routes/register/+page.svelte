<script lang="ts">
	let registrationSuccess = false;
	let email = '';
	let nickname = '';
	let password = '';
	let confirmPassword = '';
	let jmeno = '';
	let prijmeni = '';
	let datum_nar = '';
	let notification = '';

	function validatePassword(password: string) {
		const errors = [];
		if (!/[A-Z]/.test(password)) {
			errors.push('The password must contain at least one uppercase letter.');
		}
		if (!/[0-9]/.test(password)) {
			errors.push('The password must contain at least one number.');
		}
		if (password.length < 8) {
			errors.push('The password must be at least 8 characters long.');
		}
		return errors;
	}

	async function register() {
		notification = '';

		if (password !== confirmPassword) {
			notification = 'Passwords do not match.';
			return;
		}

		const passwordErrors = validatePassword(password);
		if (passwordErrors.length > 0) {
			notification = passwordErrors.join(' ');
			return;
		}

		const formData = new FormData();
		formData.append('email', email);
		formData.append('nickname', nickname);
		formData.append('password', password);
		formData.append('jmeno', jmeno);
		formData.append('prijmeni', prijmeni);
		formData.append('datum_nar', datum_nar);

		try {
			const response = await fetch('/register', {
				method: 'POST',
				body: formData,
			});

			const result = await response.json();
			if (response.ok && result.success) {
				registrationSuccess = true;
				notification = result.message;
			} else {
				notification = result.message || 'An error occurred during registration.';
			}
		} catch (error) {
			console.error('Error during registration:', error);
			notification = 'Failed to connect to the server.';
		}
	}
</script>

<div class="page-container">
	<img src="/login-back.png" class="background" alt="">
	<div class="udaje">
	<form class="registration-form" on:submit|preventDefault={register}>
		<h1>Registrace</h1>

		<label>
			Jméno
			<input type="text" bind:value={jmeno} required />
		</label>
		<label>
			Příjmení
			<input type="text" bind:value={prijmeni} required />
		</label>
		<label>
			Nickname
			<input type="text" bind:value={nickname} required />
		</label>
		<label>
			E-mail
			<input type="email" bind:value={email} required />
		</label>
		<label>
			Heslo
			<input type="password" bind:value={password} required />
		</label>
		<label>
			Potvrzení hesla
			<input type="password" bind:value={confirmPassword} required />
		</label>
		<label>
			Datum narození
			<input type="date" bind:value={datum_nar} required />
		</label>
		<button type="submit"><strong>Vytvořit účet</strong></button>
		<div>
			<a href="/login">Již máte účet?</a>
		</div>
	</form>

	{#if notification}
		<p class="notification">{notification}</p>
	{/if}

	{#if registrationSuccess}
		<p class="success">Registration successful! Check your email to verify your account.</p>
	{/if}
</div>
</div>

<style>

	.udaje {
		display: flex;
		flex-direction: column;
		align-items: center;
		padding: 20px;
	}

	.background {
		width: 100vw;
		height: 100vh;
		position: fixed;
		object-fit: cover;
		z-index: -1;
		top: 0;
		left: 0;
		filter: brightness(0.9);
	}

	.page-container {
		display: flex;
		flex-direction: column;
		align-items: center;
		justify-content: center;
		position: relative;
		height: 100vh;
		padding: 75px;
	}

	.udaje {
		display: flex;
		flex-direction: column;
		align-items: center;
		padding: 20px;
	}

	.registration-form {
		background-color: #fff;
		padding: 30px;
		border-radius: 10px;
		box-shadow: 0 4px 10px rgba(0, 0, 0, 0.2);
		width: 400px;
	}

	.registration-form h1 {
		font-size: 2em;
		color: #ff8000;
		margin-bottom: 20px;
		text-align: center;
	}

	.registration-form label {
		display: block;
		margin-bottom: 10px;
		font-size: 1.1em;
		color: #555;
	}

	.registration-form input {
		width: 100%;
		padding: 10px;
		margin-bottom: 15px;
		border: 1px solid #ddd;
		border-radius: 5px;
		font-size: 1em;
	}

	.registration-form button {
		background-color: #007bff;
		color: white;
		padding: 12px;
		border: none;
		border-radius: 5px;
		font-size: 1.2em;
		width: 100%;
		cursor: pointer;
	}

	.registration-form button:hover {
		background-color: #0056b3;
	}

	.registration-form a {
		display: block;
		margin-top: 15px;
		font-size: 0.9em;
		color: #007bff;
		text-align: center;
		text-decoration: none;
	}

	.registration-form a:hover {
		text-decoration: underline;
	}

	.notification {
		color: red;
		margin-top: 15px;
		text-align: center;
	}

	.success {
		color: green;
		margin-top: 15px;
		text-align: center;
	}

</style>


