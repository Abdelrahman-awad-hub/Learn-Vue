<template>
    <navbar
        :pages="pages"
        :activePage="activePage"
        :nav-link-click="(index) => (activePage = index)"
    />
    <page-viewer :page="pages[activePage]" />
    <creat-page :pageCreated="pageCreated" />
</template>

<script>
import PageViewer from "./components/PageViewer.vue";
import Navbar from "./components/Navbar.vue";
import CreatPage from "./components/CreatPage.vue";

export default {
    components: {
        Navbar,
        PageViewer,
        CreatPage,
    },
    data() {
        return {
            activePage: 0,
            pages: [
                {
                    links: { text: "Home", url: "home.index" },
                    pageTitle: "Home Page",
                    content: "this is home page",
                },
                {
                    links: { text: "About", url: "about.index" },
                    pageTitle: "About Page",
                    content: "this is About page",
                },
                {
                    links: { text: "contact", url: "contact.index" },
                    pageTitle: "Contact Page",
                    content: "this is contact page",
                },
            ],
        };
    },
    methods: {
        pageCreated(pageObj) {
            this.pages.push(pageObj);
        },
    },
};
</script>
