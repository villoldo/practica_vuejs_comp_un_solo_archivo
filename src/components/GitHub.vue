<template>
    <div>
        <input v-model="user" placeholder="Introduce nombre de usuario de GitHub" v-show="input" v-on:keydown="obtenerUsuario"/>
        <div class="alert alert-warning" role="alert"v-show="advertencia">
            El usuario no existe
        </div>
        <div class="card" style="width: 18rem;">
            <img class="card-img-top" src="..." alt="Card image cap">
            <div class="card-body">
                <h5 class="card-title">Card title</h5>
                <p class="card-text">Some quick example text to build on the card title and make up the bulk of the card's content.</p>
                <a href="#" class="btn btn-primary">Go somewhere</a>
                <a href="userData.html_url" class="card-link">URL de Github</a>
        </div>
</div>


    </div>
</template>

<script>

import GitHubRepos from 'GitHubRepos.vue'

export default {
    name: 'GitHub',
    components: {
        GitHubRepos
    },
    data: function() {
        return {
            input: true,    
            advertencia: false,
            card: false,
            userData: ""
        } 
    },
    methods: {
        obtenerUsuario: function() {
            // TODO: Función para obtener los datos de usuario de la API de GitHub

            // TODO: Añadir lógica para resetear los cambios en el interfaz: desactivar campo de envío,
            // resetear mensaje de error, mostrar lista de repositorios,...
                if() 

            // Obtener datos de autenticación de usuario para hacer peticiones
            // autenticadas a la API de GitHub
            var userAuth = process.env.VUE_APP_USERNAME || "villoldo";
            var passAuth = process.env.VUE_APP_USERTOKEN || "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";

            // TODO: realizar petición fetch par obtener los datos y mostrar la información en la página
            // Ejemplo de paso de datos de autorización con fetch: https://stackoverflow.com/questions/43842793/basic-authentication-with-fetch
            let url = 'https://api.github.com/users/{{user}} ';
            fetch(url,{method:'GET'})
            .then(response => {
              response.json())
             .then(data => (this.userData = data)
            });
        },
        obtenerRepositorios: function() {
            // TODO: Función para obtener los repositorios del usuario desde la API de GítHub
            // La URL de los repositorios de usuario se puede obtener a través del campo 'repos_url' de los datos del usuario

            // Obtener datos de autenticación de usuario para hacer peticiones
            // autenticadas a la API de GitHub
            var userAuth = process.env.VUE_APP_USERNAME || "villoldo";
            var passAuth = process.env.VUE_APP_USERTOKEN || "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";


            // TODO: realizar petición fetch par obtener los datos y mostrar la información en la página
            // Ejemplo de paso de datos de autorización con fetch: https://stackoverflow.com/questions/43842793/basic-authentication-with-fetch
            let url = 'https://api.github.com/users/{{user}}/repos';
            fetch (url,{method:'GET'})
            .then(response => response.json())
            .then(data => {
            const full_name = data.full_name;
            const html_url = data.html_url;
            const description = data.description;
            const forks_count = data.forks_count;
            });
        }
    }
}
</script>

<style scoped>
</style>
