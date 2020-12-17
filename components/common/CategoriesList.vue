<template>
    <div>
        <div
            v-for="category in categories"
            :key="category.cSlug"
            :class="$style.block"
        >
            <nuxt-link :to="`/category/${category.cSlug}`">
                <p>{{ category.cName }}</p>
                <img :src="category.cImage" />
            </nuxt-link>
        </div>
    </div>
</template>

<script>
export default {
    name: "CategoryList",
    props: {
        categories: {
            type: Array,
            default: () => []
        }
    }
}
</script>

<style lang="scss" module>
.wrapper {
    display: flex;
}
.block {
    display: flex;
    flex-direction: column;
}
</style>