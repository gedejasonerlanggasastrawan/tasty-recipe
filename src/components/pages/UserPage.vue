<script setup>
    import UserMenu from '../user/UserMenu.vue';
    import FavoriteRecipe from '../user/FavoriteRecipe.vue';
    import PersonalInfo from '../user/PersonalInfo.vue';
    import UserRecipe from '../user/UserRecipe.vue';

    import { useRoute } from 'vue-router';
    import { useStore } from 'vuex';
    import { computed } from 'vue';

    const route = useRoute();

    // Component mapping
    const component = {
        "personal-info": PersonalInfo,
        "favorite-recipe": FavoriteRecipe,
        "user-recipe": UserRecipe,
    }

    const getRoute = computed(() => {
        return route.params.component
    })

    const store = useStore()
    const userData = computed ( () => {
        return store.state.auth.userLogin
    })
</script>


<template>
    <div class="container-md my-5 py-5">
        <div class="row">
            <user-menu @changeComponent="$router.push($event)"></user-menu>
            <div class="col-lg-9">
                <component :is="component[getRoute]"></component>
            </div>
        </div>
    </div>
</template>

