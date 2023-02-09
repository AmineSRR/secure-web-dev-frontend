<script>

    import FilmPreview from "$lib/Film/FilmLoc.svelte";
    import { enhance } from '$app/forms';

    /** @type {import('./$types').PageData} */
    export let data;
    let create = false;
    function Create() {
        if(create) create = false
        else create = true
    }

</script>

<svelte:head>
    <title>Location</title>
</svelte:head>

<div class="home-page">
    {#if data.token}
        {#if data.user.role === 'admin'}
            <div class="test">
            <button on:click={Create}>
                Create new location
            </button>
            </div>
            {#if create}
                <form use:enhance method="POST" action="?/createLocation" class="card comment-form">
                    <div class="card-block">
                        <p>Type of movie: <textarea  name="filmType" placeholder="filmType" rows="1" >Court métrage</textarea></p>
                        <p>Name of producer : <textarea  name="filmProducerName" placeholder="filmProducerName" rows="1" >David Goodenough</textarea></p>
                        <p>End date : <textarea  name="endDate" placeholder="endDate" rows="1" >2020-08-21T00:00:00.000</textarea></p>
                        <p>Name of movie: <textarea  name="filmName" placeholder="filmName" rows="1" >C'est moche mais fonctionnel</textarea></p>
                        <p>District : <textarea  name="district" placeholder="district" rows="1" >95100</textarea></p>
                        <p>Lattitude : <textarea  name="lattitute" placeholder="lattitude" rows="1" >0</textarea></p>
                        <p>Longitude : <textarea  name="longitude" placeholder="longitude" rows="1" >0</textarea></p>
                        <p>Source location Id : <textarea  name="sourceLocationId" placeholder="sourceLocationId" rows="1" >2020-100</textarea></p>
                        <p>Director : <textarea  name="filmDirectorName" placeholder="filmDirectorName" rows="1" >David Goodenough</textarea></p>
                        <p>Adress : <textarea  name="address" placeholder="address" rows="1" >Chez michel</textarea></p>
                        <p>Start date : <textarea  name="startDate" placeholder="startDate" rows="1" >2020-07-21T00:00:00.000</textarea></p>
                        <p>Year : <textarea  name="year" placeholder="year" rows="1" >2020</textarea></p>
                    </div>

                    <div class="test">
                        <button class="btn btn-sm btn-primary" type="submit">Create location</button>
                    </div>
                </form>
                {/if}

            {/if}
        <ul class="ok">
            <div class="film-list">
                {#each data.roger as film}
                    <div class="film-item">
                        <div class="film-title">
                            <h3 class="text-primary">{film.filmName}</h3>
                        </div>
                        <div class="film-preview">
                            <FilmPreview {film} {data}/>
                        </div>
                        {#if data.user.role === 'admin'}
                            <div class="film-actions">
                                <form use:enhance method="POST" action="?/deleteLocation&id={film._id}">
                                    <button class="btn btn-danger">
                                        Delete
                                    </button>
                                </form>
                            </div>
                        {/if}
                    </div>
                {/each}
            </div>

        </ul>
        <buttons>
            <p><a href="/login" >Sign out</a></p>
        </buttons>

    {:else}
        <button>
            <a href="/login">Login please</a>
        </button>
    {/if}


</div>
<style>
    .test {
        display: flex;
        justify-content: center;
        align-items: center;
        height: 100%;
    }

    .test button {
        padding: 10px 20px;
        font-size: 18px;
        background-color: #000;
        color: #fff;
        text-decoration: none;
        border-radius: 5px;
    }

    button {
    text-decoration-color: black;
    background: bisque;
    border: 100px;
    padding: 5px;
    margin: 0;
    font-size: inherit;
    opacity: 0.6;
    cursor: pointer;
}

.buttons {
    display: flex;
    justify-content: center;
    gap: 40px;
    margin-top: 10px;
}
p {
    font-size: 18px;
    text-align: center;
    margin-top: 50px;
}

a {
    display: inline-block;
    padding: 15px 50px;
    background-color: #000;
    color: #fff;
    text-decoration: none;
    border-radius: 5px;
}

a:hover {
    background-color: #555;
}

.film-list {
    display: flex;
    flex-wrap: wrap;
    justify-content: center;
}

.film-item {
    width: 350px;
    margin: 20px;
    box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
    border-radius: 10px;
    overflow: hidden;
}

.film-title {
    background-color: #F9F9F9;
    padding: 20px;
    text-align: center;
    border-bottom: 1px solid #E9E9E9;
}

.film-preview {
    padding: 20px;
}

.film-actions {
    display: flex;
    justify-content: center;
    padding: 20px;
    border-top: 1px solid #E9E9E9;
}

.btn-danger {
    background-color: #dc3545;
    border-color: #dc3545;
    color: #fff;
    padding: 10px 20px;
    border-radius: 50px;
    font-weight: bold;
    text-transform: uppercase;
    transition: all 0.3s ease-in-out;
}

.btn-danger:hover {
    background-color: #c82333;
    border-color: #c82333;
    cursor: pointer;
}
</style>