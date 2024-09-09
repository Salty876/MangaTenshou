<script>
        import {currentUser, pb} from '../../lib/pocketbase'
        let username
        let password
        let message

        async function login(){
        try{
            const logIn = await pb.collection('users').authWithPassword(username,password)
            message = ''
            window.location.href = "/"
        }
        catch {
            message = 'Username or Password is incorrect'
            console.log(message)
      
            
        }
    }
        
    


</script>

<div class='mainFrame'>
{#if $currentUser}

    <h1 class="alrDone">Already signed in</h1>
    

{:else}

<form>
    <h1>Log In</h1>
    <input
    placeholder="Username"
    type="text"
    bind:value={username}
    >
    <input
    placeholder="Password"
    type="password"
    bind:value={password}
    >

    <button on:click={login}>
        login
    </button>
    {#if message}
    <h2>{message}</h2>
    {/if}
</form>

{/if}

</div>


<style>
    .mainFrame{
        width: 100vw;
        height: 80vh;
        display: flex;
        flex-direction: column;
        align-items: center;
        justify-content: baseline;
    }

    form{
        width: 40%;
        height: 70%;
        display: flex;
        flex-direction: column;
        /* align-items: center; */
        gap: 5%;
    }

    h1{
        color: white;
    }

    h2{
        color: white;
    }

    input{
        height: 9%;
        background-color: #71717a;
        border: none;
        border-radius: 3px;
        padding-left: 10px;


        color: white;
        font-size: 1.25rem;

    }

    input:focus{
        
        outline-style: solid;
        outline-width: 0.5vh;
        outline-color: #9333ea;
    }


    button{
        height: 10%;
        font-size: 1.5rem;
        color: white;
        background-color: #9333ea;
        border: none;
    }
    button:hover{
       
        color:#9333ea;
        background-color: #09090B;
        outline-style: solid;
        outline-width: 0.5vh;
        outline-color: #9333ea;
    }
</style>
