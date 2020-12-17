<template>
    <v-container>
        <div>
            <h1 class="center">Nuxt Test</h1>
            <CategoriesList
                :categories="categories"
                class="category-list"
            />
        </div>
    </v-container>
</template>
<script>
import CategoriesList from '~~/components/common/CategoriesList'
import { mapState } from 'vuex'
export default {
    components: {
        CategoriesList
    },
    async asyncData ({ app, route, params, error, store }) {
        try {
            await store.dispatch('getCategoriesList')
        } catch (err) {
            console.log(err)
            return error({
                statusCode: 404,
                message: 'Категории не найдены или сервер не доступен'
            })
        }
    },
    computed: {
        ...mapState({
            categories: 'categoriesList'
        })
    }
}
</script>

<style lang="scss" scoped>
    .category-list {
        display: flex;
        justify-content: space-around;
    }
</style>
