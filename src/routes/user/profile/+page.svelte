<script>
    import {currentUser, pb} from '../../../lib/pocketbase'
    import { onMount } from 'svelte';
    let uploadPpf
    let id = $currentUser.id
    let username = $currentUser.username
    let currentPassword
    let password1
    let password2
    let message = 'change password'

    const dateJoined = (($currentUser.created).split(' '))[0]

    let passOn = false

    function openPass(){

        if (passOn === false){
        passOn = true
        message = 'cancel'
        }else if(passOn === true){
            passOn = false
            message = 'change password'
        }
    }


    onMount(async() => {
       

    })


    async function login(username, password){
        await pb.collection('users').authWithPassword(username,password)
    }


    async function changePass(){
        
    

        const data = {
            "password": password1,
            "passwordConfirm": password2,
            'oldPassword': currentPassword
        }

        const record = await pb.collection('users').update($currentUser.id, data);

        login(username, password1)

        console.log(record)


    }


    async function sendAvatar(){

        console.log(uploadPpf)
        const formData = new FormData();

        formData.append('avatar', uploadPpf[0])

        console.log(formData)




    const createdRecord = await pb.collection('users').update($currentUser.id ,formData);

    }

</script>

<p>Username: {$currentUser.username}</p>
<p>Email: {$currentUser.email}</p>
<p>Date Joined: {dateJoined}</p>
<!-- {#if $currentUser.avatar}
    <img src="http://127.0.0.1:8090/api/files/users/{$currentUser.id}/{$currentUser.avatar}?thumb=100x100" alt="User Avatar">
{/if} -->


<form>
    <input
    type="file"
    placeholder="profile pic"
    bind:files={uploadPpf}
    multiple = {false}
    >

    <button on:click={sendAvatar}>set avatar</button>
</form>

<button on:click={openPass}>{message}</button>


{#if passOn}
    <form>
        <input
        type="password"
        placeholder="current password"
        bind:value={currentPassword}
    >
        <input
            type="password"
            placeholder="password"
            bind:value={password1}
        >
        <input
        type="password"
        placeholder="Condirm password"
        bind:value={password2}
    >

    <button on:click={changePass}>
        Change password
    </button>
    </form>
{/if}

