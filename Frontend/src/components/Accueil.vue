<template>
    <div class="container">
        <div class="row justify-content-center">
            <div class="col-lg-8">
                <div class="card">
                    <p class="h5 my-2 text-center">Bienvenue sur le réseau social interne</p>
                    <div class="card-header d-flex flex-column justify-content-center">
                        <img src="../assets/logo_black.svg" height="60" alt="logo groupomania">
                        <h5 class="text-center">Voici quelques informations !</h5>
                    </div>
                    <div class="card-body text-center">
                        <p>Cette application est strictement réservée au personnel du groupe.</p>
                        <p>Pour y accéder, merci de vous <router-link to="/connexion">connecter</router-link> ou de vous
                            <router-link to="/inscription">inscrire</router-link> si vous ne l'avez pas encore fait.
                        </p>
                        <p>Si vous rencontrez un problème ou si vous avez une question, rendez-vous sur la <router-link
                                to="/aide">page d'aide</router-link> ou contactez-nous via la rubrique <a
                                href="email:contactgroupomania.fr">contact.</a></p>
                    </div>
                    <div class="card-footer d-flex justify-content-center">
                        <span>Bonne navigation !</span>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    Name: "Accueil"
}
</script>

<style>
body {
    background-color: #000a41;
}
</style>