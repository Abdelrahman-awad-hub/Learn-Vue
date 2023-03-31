<template>
    <div class="container py-5">
        <h1>{{ page.pageTitle }}</h1>
        <p>{{ page.content }}</p>
    </div>
</template>

<script>
export default {
    props: ["page"],
};
</script>

<style lang="scss" scoped></style>
