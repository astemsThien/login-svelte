<script>

let userObject = null;
const userbase = window.userbase;
let authPromise = userbase.init({appId: '7e03f771-442d-4523-b503-10b2d582c494'})
	.then(({user}) => userObject = user)
let username , password ;
const signIn = () => authPromise = userbase.signIn({username, password}).then(user => userObject = user);
const signUp = () => authPromise = userbase.signUp({username, password}).then(user => userObject = user);
const signOut = () => authPromise = userbase.signOut().then(() => userObject = null)
// let login = open;
// const open = () => document.getElementById("content").style.display = 'block';

</script>
<button style="width: 20%; margin: 0 auto;font-size: 25px; padding: 10px; background-color: cadetblue;border: 1px solid cadetblue; border-radius: 5px; color: whitesmoke; display: flex; justify-content: center; align-items: center;cursor: pointer;" type="button" on:click={open}>Hãy click vào đây!!!</button>


{#await authPromise}Loading...{:then _}
{#if !userObject}

<form id="content" style="display: none;width: 20%; margin: 120px auto; border: 1px solid blanchedalmond;padding: 10px; background-color: blanchedalmond;">
	<h1 style="display: flex;justify-content: center; align-items: center;color:palevioletred ;">Vina_Astems</h1>
	<label for="username" style="font-size: 20px; font-weight: 900; color: blue;">Username:</label>
	<input id="username" style="font-size: 18px; margin: 10px 0 10px 25px;" type="text" bind:value={username}><br>
	<label for="password" style="font-size: 20px; font-weight: 900; color: blue;">Password:</label>
	<input id="password" style="font-size: 18px; margin: 0 0 0 29px;" type="password" bind:value={password}><br>
	<div class="btn-item" style="width: 100%;display: flex;">
		<button on:click={signIn} type="button" style="width: 50%; background-color: skyblue; color: white; border: 1px solid; border-radius: 20px; font-size: 25px; margin: 20px 10px 10px 0;">Sign in</button>
		<button on:click={signUp} type="button" style="width: 50%; background-color: green; color: white; border: 1px solid; border-radius: 20px; font-size: 25px; margin: 20px 10px 10px 0;">Sign up</button>
	</div>
	</form>
{:else}
	<h1 style="display: flex;justify-content: center; align-items: center;color:palevioletred ;width: 100%;height: 100vh; font-size: 80px;">Hi, {userObject.username.toUpperCase()}!</h1>
	<button on:click={signOut} style="position: absolute; top: 10px; right: 10px;background-color: gray; color: white; border: 1px solid;border-radius: 5px; font-size: 20px; cursor: pointer;"><i class="fa-solid fa-right-from-bracket"></i></button>
{/if}
{:catch error} Error! {error} {/await}
