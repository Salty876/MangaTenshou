<!-- <a href="/login">login</a>
<a href="/signUp">sign up</a>
<a href="/">Home</a>
<a href="/user/profile">profile</a> -->
<script>

    import {currentUser, pb} from '../lib/pocketbase'


    let searchValue
    let searchBarStatus = false

    

</script>


<nav class='nav'>
    <div class="leftSide" >

    <!-- Where the sandwich menu goes -->
    <h3>MangaTensou</h3>
    <!-- Where the logo goes -->
    </div>

    <div class="rightSide" >
        <div class='searchContainer'>
            <input
                class="searchbar"
                type="text"
                bind:value={searchValue}
          
            >
            <button>
                <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 512 512"><!--!Font Awesome Free 6.6.0 by @fontawesome - https://fontawesome.com License - https://fontawesome.com/license/free Copyright 2024 Fonticons, Inc.--><path fill="#ffffff" d="M416 208c0 45.9-14.9 88.3-40 122.7L502.6 457.4c12.5 12.5 12.5 32.8 0 45.3s-32.8 12.5-45.3 0L330.7 376c-34.4 25.2-76.8 40-122.7 40C93.1 416 0 322.9 0 208S93.1 0 208 0S416 93.1 416 208zM208 352a144 144 0 1 0 0-288 144 144 0 1 0 0 288z"/></svg>
            </button>
        </div>

        {#if $currentUser}
            <div class="dropdown">
                <a href="/">
                    <img class='profilePicture' src="http://127.0.0.1:8090/api/files/users/{$currentUser.id}/{$currentUser.avatar}?thumb=50x50" alt="pfp">
                </a>
                <div class='dropdownContent'>
                   <div class="nameAndPfp">
                    <img class='profilePicture' src="http://127.0.0.1:8090/api/files/users/{$currentUser.id}/{$currentUser.avatar}?thumb=50x50" alt="pfp">
                    <h3>{$currentUser.username}</h3>
                   </div>

                   <hr>

                   <ul>
                        <li>
                            <a href="/user/profile">profile</a>
                        </li>

                        <li>
                            <a href="/user/readlist">My list</a>
                        </li>

                        <li>
                            <a href="/user/settings">Settings</a>
                        </li>
                   </ul>
                </div>
            </div>
        {/if}
    </div>

</nav>



<slot></slot>

<style>
    :global(body){
        margin: 0;

        }
    nav{
        display: flex;
        flex-direction: row;
        align-items: center;
        justify-content: space-between;

        width:  calc(100% - 6vw);
        height: 8vh;

        background-color: #27272A;

        
        padding-left: 3vw;
        padding-right: 3vw;

    }

    button{
        width: 2vw;
        background-color: #71717a;
        border: none;
        display: flex;
        justify-content: center;
        align-items: center;
        border-radius: 10px;

    }

    .rightSide{
        display: flex;
        flex-direction: row;
        align-items: center;
        justify-content: space-between;
        gap:2vw;
    }

    .searchContainer{
        width: 20vw;
        height: 4vh;
        background-color: #71717a;

        display: flex;
        flex-direction: row;
        border-radius: 10px;

        transition-property: width;
        transition-duration: 0.2s;
        transition-timing-function: ease-out;
        transition-delay: 0s;
        padding-right: 10px;

    }



    input{
        flex-grow: 2;
        outline: 1vh;
        outline-style: none;
        border: none;
        background-color: #71717a;
        border-radius: 20px;
        padding-left: 10px;


        
        }



        .searchContainer:focus-within{
        outline: 0.2rem;
        width: 40vw;
        outline-style: solid;
        outline-color: #9333ea;
     
    }

    .profilePicture{
        border-radius:30px ;
        
    }

    .dropdown{
        display: inline-block;
        justify-content: center;
        margin: 1vw;
        
    }

    .dropdownContent{
        display: none;
        min-width: 20vw;
        height: 50vh;
        background-color: #262626;
    
    }

    .dropdown:hover .dropdownContent{
        display: flex;
        flex-direction: column;
        align-items: center;
        position: absolute;
        right: 0;

    }


    hr{
        width: 90%;
    }
</style>
