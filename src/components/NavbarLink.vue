<template>
    <a
        class="nav-link"
        aria-current="page"
        :href="page.links.url"
        :class="{ active: isActive }"
    >
        {{ page.links.text }}
    </a>
</template>

<script>
export default {
    props: ["page", "isActive"],
};
</script>

<style scoped>
.active {
    text-decoration: underline;
}
</style>
