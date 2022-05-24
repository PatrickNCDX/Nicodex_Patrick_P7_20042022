<template>
    <div>
        <div class="container">
            <div class="row justify-content-center">
                <div class="col-lg-8">
                    <router-link to="/messages" class="my-2 btn btn-success">...retour aux messages
                    </router-link>
                </div>
                <div class="col-lg-8">
                    <div class="card">
                        <div class="card-header text-center">
                            <span class="h5">{{ userName }}</span>
                        </div>
                        <div class="card-body" style="background-color:lightgrey;">
                            <div class="d-flex align-items-center" style="background-color: white;">
                                <div class="text-center">
                                    <img :src="avatar" height="150" />
                                    <a href="" class="btn btn-primary mb-2" data-toggle="modal"
                                        data-target="#modalAvatar">Changer de photo</a>
                                </div>
                                <div class="modal fade" id="modalAvatar" aria-labelledby="modalAvatar"
                                    aria-hidden="true">
                                    <div class="modal-dialog">
                                        <div class="modal-content">
                                            <form @submit.prevent="updateAvatar()" enctype="multipart/form-data">
                                                <div class="modal-header">
                                                    <p class="modal-title h5">Changer la photo de profile
                                                    </p>
                                                </div>
                                                <div class="row modal-body">
                                                    <div class="col-6 justify-content-center">
                                                        <img :src="avatar" class="w-100">
                                                        <p class="text-center">Photo actuelle</p>
                                                    </div>
                                                    <div class="col-6 justify-content-center">
                                                        <img :src="newAvatar" class="w-100">
                                                        <p class="text-center">Nouvelle photo</p>
                                                    </div>
                                                    <div class="col-12">
                                                        <div class="form-group justify-content-center">
                                                            <label for="File" class="sr-only">Choisir une nouvelle
                                                                photo</label>
                                                            <input @change="onFileChange()" type="file" ref="file"
                                                                name="image" class="form-control-file" id="File"
                                                                accept=".jpg, .jpeg, .gif, .png"
                                                                :class="{ 'is-invalid': submitted && !file }">
                                                            <div v-show="submitted && !file" class="invalid-feedback">
                                                                Une nouvelle photo est requise !</div>
                                                        </div>
                                                    </div>
                                                </div>
                                                <div class="modal-footer">
                                                    <div class="row w-100 justify-content-spacebetween">
                                                        <div class="col-6"><a data-dismiss="modal"
                                                                class="btn btn-secondary btn-block">Annuler</a>
                                                        </div>
                                                        <div class="col-6"><button type="submit"
                                                                class="btn btn-success btn-block">Valider</button>
                                                        </div>
                                                    </div>
                                                </div>
                                            </form>
                                        </div>
                                    </div>
                                </div>
                                <div class="col-md-8">
                                    <p class="text-left m-2">Adresse e-mail : {{ email }}</p>
                                    <p class="text-left m-2">Rôle : {{ role }}</p>
                                    <p class="text-left m-2">Crée le : {{ createdAt }}</p>
                                    <p class="text-left m-2">Votre contenu : </p>
                                    <ul>
                                        <li class="text-left m-2"><a href="#/compte/messages">{{ messagesCount
                                        }} message<span v-if="messagesCount > 1">s</span></a></li>
                                        <li class="text-left m-2">{{ commentsCount }} commentaire<span
                                                v-if="commentsCount > 1">s</span></li>
                                    </ul>
                                </div>
                            </div>
                        </div>
                        <div class="card-footer">
                            <div class="d-flex align-items-center">
                                <div class="col-12">
                                    <a href="" data-toggle="modal" data-target="#modalDeleteAccount"
                                        class="btn btn-block btn-danger">Supprimer mon compte !</a>
                                    <div class="modal fade" id="modalDeleteAccount" data-backdrop="static"
                                        data-keyboard="false" tabindex="-1" aria-labelledby="modalDeleteAccount"
                                        aria-hidden="true">
                                        <div class="modal-dialog modal-dialog-centered">
                                            <div class="modal-content border border-danger">
                                                <form enctype="multipart/form-data">
                                                    <div class="modal-header">
                                                        <p class="modal-title h5 text-danger">Supprimer mon compte ?</p>
                                                    </div>
                                                    <div class="row modal-body">
                                                        <div class="col-12 form-group">
                                                            <p class="text-danger"><span class="h6">ATTENTION !</span>
                                                                Cette action est irreversible.</p>
                                                            <p>Vous ne pourrez plus vous connecter avec cette adresse
                                                                mail, mais vos messages et commentaires seront toujours
                                                                visible par les autres utilisateurs.</p>
                                                            <p>Êtes-vous <span class="font-weight-bold">certain</span>
                                                                de vouloir supprimer votre compte ?</p>
                                                        </div>
                                                    </div>
                                                    <div class="modal-footer">
                                                        <div class="row w-100 justify-content-spacebetween">
                                                            <div class="col-6"><a data-dismiss="modal"
                                                                    class="btn btn-secondary btn-block">Annuler</a>
                                                            </div>
                                                            <div class="col-6"><button type="submit"
                                                                    @click.prevent="deleteAccount()"
                                                                    class="btn btn-danger btn-block">Valider</button>
                                                            </div>
                                                        </div>
                                                    </div>
                                                </form>
                                            </div>
                                        </div>
                                    </div>
                                </div>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
import axios from "axios"
import Swal from "sweetalert2"

export default {
    name: "Compte",
    data() {
        return {
            userName: "",
            email: "",
            role: "",
            createdAt: "",
            messagesCount: "",
            commentsCount: "",
            avatar: "",
            newAvatar: "/images/avatars/default_user.jpg",
            file: null,
            submitted: false
        }
    },
    methods: {
        onFileChange() {
            this.file = this.$refs.file.files[0];
            this.newAvatar = URL.createObjectURL(this.file)
        },
        updateAvatar() {
            this.submitted = true
            const formData = new FormData()
            formData.append("image", this.file);
            axios.put("http://127.0.0.1:3000/api/users/" + localStorage.getItem("userId"), formData, { headers: { "Authorization": "Bearer " + localStorage.getItem("token") } })
                .then(function (res) {
                    localStorage.setItem("avatar", res.data.avatar)
                    Swal.fire({
                        text: "La photo de profil à été mise à jour !",
                        footer: "Redirection en cours...",
                        icon: "success",
                        timer: 1000,
                        showConfirmButton: false,
                        timerProgressBar: true,
                        willClose: () => { location.reload() }
                    })
                })
                .catch(function (error) {
                    const codeError = error.message.split("code ")[1]
                    let messageError = ""
                    switch (codeError) {
                        case "400": messageError = "La photo de profil n'a pas été mise à jour !"; break
                        case "401": messageError = "Requête non-authentifiée !"; break
                    }
                    Swal.fire({
                        title: "Une erreur est survenue",
                        text: messageError || error.message,
                        icon: "error",
                        timer: 1500,
                        showConfirmButton: false,
                        timerProgressBar: true
                    })
                })
        },
        deleteAccount() {
            axios.put("http://127.0.0.1:3000/api/users/" + localStorage.getItem("userId"), { isActive: false }, { headers: { "Authorization": "Bearer " + localStorage.getItem("token") } })
                .then(() => {
                    localStorage.clear()
                    Swal.fire({
                        text: "Le compte à été supprimé !",
                        footer: "Déconnexion en cours...",
                        icon: "success",
                        timer: 5000,
                        showConfirmButton: false,
                        timerProgressBar: true,
                        willClose: () => { location.reload() }
                    })
                })
                .catch(function (error) {
                    const codeError = error.message.split("code ")[1]
                    let messageError = ""
                    switch (codeError) {
                        case "400": messageError = "La photo de profil n'a pas été mise à jour !"; break
                        case "401": messageError = "Requête non-authentifiée !"; break
                    }
                    Swal.fire({
                        title: "Une erreur est survenue",
                        text: messageError || error.message,
                        icon: "error",
                        timer: 1500,
                        showConfirmButton: false,
                        timerProgressBar: true
                    })
                })
        }
    },
    created: function () {
        axios.get("http://127.0.0.1:3000/api/users/" + localStorage.getItem("userId"), { headers: { "Authorization": "Bearer " + localStorage.getItem("token") } })
            .then(user => {
                this.userName = user.data.userName
                this.email = user.data.email
                this.role = user.data.role
                this.createdAt = user.data.createdAt.slice(0, 10).split('-').reverse().join('/') + ' à ' + user.data.createdAt.slice(11, 16)
                this.messagesCount = user.data.messagesCount
                this.commentsCount = user.data.commentsCount
                this.avatar = user.data.avatar
            })
            .catch(function (error) {
                const codeError = error.message.split("code ")[1]
                let messageError = ""
                switch (codeError) {
                    case "400": messageError = "Vos informations non pas été récuperées !"; break
                    case "401": messageError = "Requête non-authentifiée !"; break
                }
                Swal.fire({
                    title: "Une erreur est survenue",
                    text: messageError || error.message,
                    icon: "error",
                    timer: 1500,
                    showConfirmButton: false,
                    timerProgressBar: true
                })
            })
    }
}
</script>

<style>
body {
    background-color: #000a41;
}
</style>
