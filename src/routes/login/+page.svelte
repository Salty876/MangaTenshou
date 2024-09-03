<script>
        import {currentUser, pb} from '../../lib/pocketbase'
        let username
        let password

        async function login(){
        await pb.collection('users').authWithPassword(username,password)
    }

    function logout(){
        pb.authStore.clear()
    }

</script>


{#if $currentUser}

    <p>Already signed in as {$currentUser.username}</p>
    

{:else}

<form>
    <input
    placeholder="username"
    type="text"
    bind:value={username}
    >
    <input
    placeholder="password"
    type="text"
    bind:value={password}
    >

    <button on:click={login}>
        login
    </button>
</form>
{/if}

<button on:click={logout}>
    logout
</button>



