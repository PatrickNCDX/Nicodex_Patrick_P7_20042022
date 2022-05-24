<template>
    <div>
        <div class="container">
            <div class="row justify-content-center">
                <div class="col-lg-8">
                    <router-link v-if="isLogged" to="/messages" class="my-2 btn btn-success">...retour
                        aux messages</router-link>
                    <div class="card">
                        <div class="card-header d-flex flex-column justify-content-center">
                            <p class="h5 text-center">Bienvenue sur la page d'aide</p>
                            <p class="h5 text-center">Quel est votre problème ?</p>
                        </div>
                        <div class="card-body">
                            <div class="accordion" id="accordionExample">
                                <div class="card border-0">
                                    <div class="m-1" id="headingOne">
                                        <h2 class="card">
                                            <button class="btn-sm btn-block btn-primary text-center" type="button"
                                                data-toggle="collapse" data-target="#collapseOne" aria-expanded="false"
                                                aria-controls="collapseOne">
                                                Connexion et Inscription
                                            </button>
                                        </h2>
                                    </div>
                                    <div id="collapseOne" class="collapse" aria-labelledby="headingOne"
                                        data-parent="#accordionExample">
                                        <div class="card-body">
                                            <p class="h5 text-center">Comment s'inscrire ?</p>
                                            <ul>
                                                <li>Rendez-vous sur la page d'accueil et choisissez
                                                    "Inscrivez-vous" ou via le menu en haut à droite.</li>
                                                <li>Remplissez le formulaire avec un nom d'utilisateur,
                                                    une adresse mail et un mot de passe.</li>
                                                <li>Validez et le tour est joué !</li>
                                                <li>NB: Une photo de profil par défaut vous
                                                    sera attribuée. Vous pourrez la modifier plus tard.</li>
                                            </ul>
                                            <p class="h5 text-center">Comment se connecter ?</p>
                                            <ul>
                                                <li>Rendez-vous sur la page d'accueil et choisissez
                                                    "Connectez-vous" ou via le menu en haut à droite.</li>
                                                <li>Remplissez le formulaire avec l'adresse mail et le
                                                    mot de passe utilisés lors de l'inscription.</li>
                                                <li>Validez et le tour est joué !</li>
                                            </ul>
                                        </div>
                                    </div>
                                </div>
                                <div class="card border-0">
                                    <div class="m-1" id="headingTwo">
                                        <h2 class="card">
                                            <button class="btn-sm btn-block btn-primary text-center" type="button"
                                                data-toggle="collapse" data-target="#collapseTwo" aria-expanded="false"
                                                aria-controls="collapseTwo">
                                                Les messages
                                            </button>
                                        </h2>
                                    </div>
                                    <div id="collapseTwo" class="collapse" aria-labelledby="headingTwo"
                                        data-parent="#accordionExample">
                                        <div class="card-body">
                                            <div class="alert alert-danger" role="alert">
                                                À tout moment, un administrateur peut modifier ou supprimer un de vos
                                                messages si le contenu n'est pas approprié !
                                            </div>
                                            <p class="h5 text-center">Comment publier un message ?</p>
                                            <ul>
                                                <li>Une fois connecté, vous arriverez directement sur le
                                                    fil de messages.</li>
                                                <li>Pour publier un nouveau message, cliquer sur le bouton
                                                    "Poster un message".</li>
                                                <li>Remplissez les champs.</li>
                                                <li>Validez et le message est publié !</li>
                                                <li>NB: Vous pouvez soit remplir le champ de texte,
                                                    soit choissir une image ou bien les deux.</li>
                                            </ul>
                                            <p class="h5 text-center">Comment modifier un message ?</p>
                                            <ul>
                                                <li>Si vous êtes le propriétaire du message, un menu
                                                    apparaîtra à droite du message vous offrant la possibilité de le
                                                    modifier ou de le supprimer.</li>
                                                <li>Pour modifier le message, cliquez sur l'icône <img
                                                        src="/images/modify.svg"></li>
                                                <li>Remplissez le champ de texte et/ou de l'image.</li>
                                                <li>Validez et le message est modifié !</li>
                                                <li>NB: Pour le moment, il n'est pas possible
                                                    de supprimer l'image du message.</li>
                                            </ul>
                                            <p class="h5 text-center">Comment supprimer un message ?</p>
                                            <ul>
                                                <li>Si vous êtes le propriétaire du message, un menu
                                                    apparaîtra à droite du message vous offrant la possibilité de le
                                                    modifier ou de le supprimer.</li>
                                                <li>Pour modifier le message, cliquez sur l'icône <img
                                                        src="/images/delete.svg"></li>
                                                <li>Une fenêtre de confirmation apparaît avec le message.
                                                </li>
                                                <li>Validez et le message est supprimé !</li>
                                                <li class="text-danger">NB: Supprimer un message entraînera la
                                                    suppression de tous les commentaires associés.</li>
                                            </ul>
                                        </div>
                                    </div>
                                </div>
                                <div class="card border-0">
                                    <div class="m-1" id="headingThree">
                                        <h2 class="card">
                                            <button class="btn-sm btn-block btn-primary text-center" type="button"
                                                data-toggle="collapse" data-target="#collapseThree"
                                                aria-expanded="false" aria-controls="collapseThree">
                                                Les commentaires
                                            </button>
                                        </h2>
                                    </div>
                                    <div id="collapseThree" class="collapse" aria-labelledby="headingThree"
                                        data-parent="#accordionExample">
                                        <div class="card-body">
                                            <div class="alert alert-danger" role="alert">
                                                À tout moment, un administrateur peut modifier ou supprimer un de vos
                                                commentaires si le contenu n'est pas approprié !
                                            </div>
                                            <p class="h5 text-center">Comment lire les commentaires ?</p>
                                            <ul>
                                                <li>Cliquez sur le lien au bas d'un message pour accéder
                                                    aux commentaires.</li>
                                            </ul>
                                            <p class="h5 text-center">Comment publier un commentaire ?</p>
                                            <ul>
                                                <li>Pour publier un nouveau commentaire, cliquer sur le
                                                    bouton "Poster un commentaire".</li>
                                                <li>Replissez le champ de texte.</li>
                                                <li>Validez et le commentaire est publié !</li>
                                                <li>NB: Vous ne pouvez pas poster d'image
                                                    dans un commentaire.</li>
                                            </ul>
                                            <p class="h5 text-center">Comment modifier un commentaire ?</p>
                                            <ul>
                                                <li>Si vous êtes le propriétaire du commentaire, un menu
                                                    apparaîtra à droite du commentaire vous offrant la possibilité de le
                                                    modifier ou de le supprimer.</li>
                                                <li>Pour modifier le commentaire, cliquez sur l'icône <img
                                                        src="/images/modify.svg"></li>
                                                <li>Remplissez le champ de texte.</li>
                                                <li>Validez et le commentaire est modifié !</li>
                                            </ul>
                                            <p class="h5 text-center">Comment supprimer un commentaire ?</p>
                                            <ul>
                                                <li>Si vous êtes le propriétaire du commentaire, un menu
                                                    apparaîtra à droite du commentaire vous offrant la possibilité de le
                                                    modifier ou de le supprimer.</li>
                                                <li>Pour modifier le commentaire, cliquez sur l'icône <img
                                                        src="/images/delete.svg"></li>
                                                <li>Une fenêtre de confirmation apparaît avec le
                                                    commentaire.</li>
                                                <li>Validez et le commentaire est supprimé !</li>
                                            </ul>
                                        </div>
                                    </div>
                                </div>
                                <div class="card border-0">
                                    <div class="m-1" id="headingFour">
                                        <h2 class="card">
                                            <button class="btn-sm btn-block btn-primary text-center" type="button"
                                                data-toggle="collapse" data-target="#collapseFour" aria-expanded="false"
                                                aria-controls="collapseFour">
                                                Mon compte
                                            </button>
                                        </h2>
                                    </div>
                                    <div id="collapseFour" class="collapse" aria-labelledby="headingFour"
                                        data-parent="#accordionExample">
                                        <div class="card-body">
                                            <p class="h5 text-center">Comment me déconnecter ?</p>
                                            <ul>
                                                <li>Rendez-vous sur votre menu en haut à droite.</li>
                                                <li>Choisissez "Déconnexion".</li>
                                                <li>Validez et le tour est joué !</li>
                                            </ul>
                                            <p class="h5 text-center">Comment modifier ma photo de profil ?</p>
                                            <ul>
                                                <li>Rendez-vous sur votre menu en haut à droite.</li>
                                                <li>Choisissez "Mon compte".</li>
                                                <li>Choisissez "Changer de photo".</li>
                                                <li>Choisissez une nouvelle photo.</li>
                                                <li>Validez et le tour est joué !</li>
                                            </ul>
                                            <p class="h5 text-center">Comment voir tous mes messages ?</p>
                                            <ul>
                                                <li>Rendez-vous sur votre menu en haut à droite.</li>
                                                <li>Choisissez "Mes messages".</li>
                                                <li>Vous serez envoyé vers une page contenant tous vos
                                                    messages !</li>
                                            </ul>
                                            <p class="h5 text-center">Comment supprimer mon compte ?</p>
                                            <ul>
                                                <li>Rendez-vous sur votre menu en haut à droite.</li>
                                                <li>Choisissez "Mon compte".</li>
                                                <li>Choisissez "Supprimer mon compte".</li>
                                                <li>Une fenêtre de confirmation apparaît.</li>
                                                <li>Validez et votre compte sera supprimé et vous serez
                                                    automatiquement déconnecté !</li>
                                                <li class="text-danger">NB: Vous ne pourrez plus vous connecter
                                                    avec cette adresse mail, mais vos messages et commentaires seront
                                                    toujours visible par les autres utilisateurs.</li>
                                            </ul>
                                        </div>
                                    </div>
                                </div>
                            </div>
                        </div>
                        <div v-if="!isLogged" class="card-footer">
                            <router-link to="/connexion">Connectez-vous</router-link> ou
                            <router-link to="/inscription">Inscrivez-vous</router-link> !
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    Name: "Aide",
    computed: {
        isLogged() {
            if (localStorage.getItem("token") !== null) {
                return true
            }
            return false
        }
    }
}
</script>

<style>
body {
    background-color: #000a41;
}
</style>