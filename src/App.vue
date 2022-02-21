<template>
    <div id="app">
        <h1 class="text-center mb-2">Buscar usuario de GitHub</h1>
    </div>
</template>

<script>
import GitHub from './components/GitHub.vue'
import GitHubRepos from './components/GitHubRepos.vue'

export default {
    name: 'App',
    components: {
      GitHub,
      GitHubRepos
    }
}
</script>

<style>
</style>
