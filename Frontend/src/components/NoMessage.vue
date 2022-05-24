<template>
    <div class="card">
        <p class="h5 my-3 text-center">Bienvenue sur le réseau social interne</p>
        <div class="card-header d-flex justify-content-center">
            <img src="../assets/logo_black.svg" class="w-75" alt="logo groupomania">
        </div>
        <div class="card-body d-flex flex-column flex-md-row text-center align-items-center p-1 m-1">
            <div class="col-12 col-md-9 mt-3">
                <p>Vous êtes la première personne à vous connecter, félicitations !</p>
                <p>Il n'y a aucun message à lire pour le moment...</p>
                <p>À vous de commencer en postant le premier message !</p>
            </div>
            <div class="col-12 col-md-3 text-center">
                <img src="/images/modify.svg" width="50" height="50">
            </div>
        </div>
    </div>
</template>

<script>
export default {
    Name: "NoMessage"
}
</script>