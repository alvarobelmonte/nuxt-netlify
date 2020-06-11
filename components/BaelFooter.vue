<template>
<footer class="xs-text-6 md-text-5 pt-6 pb-6">
    <div class="r no-gap">

        <div class="xs-text-left xs-p2 xs-border" :class="signupAboutSize">
            <div class="item">
                <div v-show="siteDescription" class="footer__heading xs-mb2">About</div>
                <p v-show="siteDescription">{{siteDescription}}</p>
            </div>
        </div>

        <div class="c-12 xs-text-left xs-p2 xs-border">
            <div class="item xs-text-6"><a href="https://github.com/jake-101/bael-template">Based on Bael</a>, An open source design by
                <a href="https://jake101.com">jake101</a>
            </div>
        </div>
    </div>
</footer>
</template>

<script>
export default {
    props: ["pagination"],
    watchQuery: ['page'],
    data() {
        return {
            emaildata: {
                email: ""
            },
            sent: false
        };
    },
    methods: {

        async processForm() {
            try {
                const sendgrid = await this.$axios.post(
                    `${process.env.API_URL}/.netlify/functions/app`,
                    this.emaildata
                );
                console.log("Processed!");
                this.sent = true;
            } catch (e) {
                console.log(e);
            }
        }
    },
    computed: {
        nextCheck() {
            if (this.nextpage > this.queryParam) {
                return true
            } else {
                return false
            }
        },
        pageCount() {
            var tp = (this.$store.state.gridNumPosts * 1) + (this.$store.state.gridOffset * 1)
            if (tp > this.$store.state.resultsnum) {
                return this.$store.state.resultsnum

            } else {
                return tp + 1

            }
        },
        signupAboutSize: function () {
            return {
                "c-25": this.signupBoolean,
                "c-4": !this.signupBoolean
            };
        },
        prevpage() {
            var prev = Number(this.queryParam) - 1;
            return prev;
        },
        totalpages() {
            var res = this.$store.state.resultsnum;
            var total = Math.ceil(res / 12);
            return total;
        },
        nextpage() {
            var next = Number(this.queryParam) + 1;
            return next;
        },
        queryParam() {
            if (this.$route.query.page == null) {
                return 1;
            } else {
                return Number(this.$route.query.page);
            }
        },

        connectData() {
            return this.$store.state.connect.connectlinks;
        },
        siteDescription() {
            return this.$store.state.siteInfo.sitedescription;
        },
        signupBoolean() {
            return this.$store.state.siteInfo.emailsignup;
        }
    }
};
</script>

<style scoped>
footer {
    background-color: black;
    color: white;
}
.text-input {
    max-width: 100%;
}

.footer__heading {
    max-width: 100%;
}
</style>
