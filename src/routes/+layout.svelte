<!-- <a href="/login">login</a>
<a href="/signUp">sign up</a>
<a href="/">Home</a>
<a href="/user/profile">profile</a> -->
<script>

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


    .searchContainer{
        width: 30vw;
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
        width: 50vw;
        outline-style: solid;
        outline-color: #9333ea;
     
    }
</style>
