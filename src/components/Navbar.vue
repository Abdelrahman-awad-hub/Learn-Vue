<template>
    <nav
        class="navbar navbar-expand-lg"
        :class="[`navbar-${theme}`, `bg-${theme}`]"
    >
        <div class="container">
            <a class="navbar-brand" href="#">Vue</a>
            <button
                class="navbar-toggler"
                type="button"
                data-bs-toggle="collapse"
                data-bs-target="#navbarNav"
                aria-controls="navbarNav"
                aria-expanded="false"
                aria-label="Toggle navigation"
            >
                <span class="navbar-toggler-icon"></span>
            </button>
            <div
                class="collapse navbar-collapse justify-content-between"
                id="navbarNav"
            >
                <ul class="navbar-nav">
                    <li
                        v-for="(page, index) in pages"
                        class="nav-item"
                        :key="index"
                    >
                        <NavbarLink
                            @click.prevent="navLinkClick(index)"
                            :isActive="activePage == index"
                            :page="page"
                        />
                    </li>
                </ul>
                <form class="d-flex">
                    <button
                        class="btn btn-primary"
                        @click.prevent="changTheme()"
                    >
                        navbar bg color
                    </button>
                </form>
            </div>
        </div>
    </nav>
</template>

<script>
import NavbarLink from "./NavbarLink.vue";

export default {
    components: {
        NavbarLink,
    },
    created() {
        this.getNvbarTheme();
    },
    props: ["pages", "activePage", "navLinkClick"],
    data() {
        return {
            theme: "dark",
        };
    },
    methods: {
        changTheme() {
            let theme = "dark";
            if (this.theme === "dark") {
                theme = "light";
            }
            this.theme = theme;
            this.setNvbarTheme();
        },
        setNvbarTheme() {
            localStorage.setItem("theme", this.theme);
        },
        getNvbarTheme() {
            let theme = localStorage.getItem("theme");
            if (theme) {
                this.theme = theme;
            }
        },
    },
};
</script>
