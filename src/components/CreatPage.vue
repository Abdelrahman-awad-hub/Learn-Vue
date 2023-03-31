<template>
    <form class="container py-5 row">
        <div class="col-5">
            <div class="mb-3">
                <label for="exampleFormControlTextarea1" class="form-label"
                    >Page Title
                </label>
                <input
                    class="form-control form-control-lg"
                    type="text"
                    placeholder="Page Title"
                    v-model="pageTitle"
                />
            </div>
            <div class="mb-3">
                <label for="exampleFormControlTextarea1" class="form-label"
                    >Page Content</label
                >
                <textarea
                    class="form-control"
                    id="exampleFormControlTextarea1"
                    rows="3"
                    placeholder="Page Content"
                    v-model="content"
                ></textarea>
            </div>
        </div>
        <div class="col-5">
            <div class="mb-3">
                <label for="exampleFormControlTextarea1" class="form-label"
                    >Link Name</label
                >
                <input
                    class="form-control form-control-lg"
                    type="text"
                    placeholder="Link name"
                    v-model="linkName"
                />
            </div>
            <div class="mb-3">
                <label for="exampleFormControlTextarea1" class="form-label"
                    >Link URL</label
                >
                <input
                    class="form-control form-control-lg"
                    type="text"
                    placeholder="URL"
                    v-model="linkUrl"
                />
            </div>
            <div class="form-check">
                <input
                    class="form-check-input"
                    type="checkbox"
                    value=""
                    id="flexCheckDefault"
                />
                <label class="form-check-label" for="flexCheckDefault">
                    published
                </label>
            </div>
            <button
                class="btn btn-primary"
                :disabled="isFormInvalid"
                @click.prevent="submitForm"
            >
                Craete Page
            </button>
        </div>
    </form>
</template>

<script>
export default {
    props: ["pageCreated"],
    computed: {
        isFormInvalid() {
            return (
                !this.pageTitle ||
                !this.content ||
                !this.linkName ||
                !this.linkUrl
            );
        },
    },
    data() {
        return {
            pageTitle: "",
            content: "",
            linkName: "",
            linkUrl: "",
        };
    },
    methods: {
        submitForm() {
            if (
                !this.pageTitle ||
                !this.content ||
                !this.linkName ||
                !this.linkUrl
            ) {
                alert("you maste fill all form data");
                return 0;
            }
            this.pageCreated({
                pageTitle: this.pageTitle,
                content: this.content,
                links: {
                    text: this.linkName,
                    url: this.linkUrl,
                },
            });
        },
    },
    watch: {
        pageTitle(newTitle, oldTitle) {
            if (this.linkName === oldTitle) {
                this.linkName = newTitle;
            }
        },
    },
};
</script>
<style lang="scss" scoped></style>
