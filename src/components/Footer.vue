<template>
    <footer class="footer">
        <hr>
        <div class="">
            <div class="columns has-text-centered">
                <div class="column is-one fifth">

                </div>
                <div class="column is-one fifth">
                    <a href="#" @click="this.toggleAboutModal">About</a>
                </div>
                <div class="column is-one fifth">
                    <svg id="Layer_1" data-name="Layer 1" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 148.64 63.1">
                        <title>am logos final</title>
                        <path class="cls-1" d="M307,396.15h-6.16l-28.29-61h5.57Z" transform="translate(-229.08 -334.57)"/>
                        <path class="cls-2" d="M258.82,335.15h5l-28.95,61h-5Z" transform="translate(-229.08 -334.57)"/>
                        <path class="cls-3" d="M307.83,396.66l8.87-62.09h1l25.18,50.95,24.94-50.95h1l8.91,62.09h-6.07l-6.12-44.4-21.89,44.4h-1.59l-22.16-44.74-6.08,44.74Z" transform="translate(-229.08 -334.57)"/>
                        <path class="cls-2" d="M272.11,335.15h5.57l-28.36,61h-6.16Z" transform="translate(-229.08 -334.57)"/>
                    </svg>
                    <p class="help">desgined and built by Ari Madian</p>
                </div>
                <div class="column is-one fifth">
                    <a href="#" @click="this.toggleLegalModal">Legal</a>
                </div>
                <div class="column is-one fifth">

                </div>
            </div>
        </div>
    </footer>
</template>
<script>
export default {
    name: 'Footer',
    props: ['value'],
    data: function() {
        return {
            aboutActive: this.value
        }
    },
    methods: {
        toggleAboutModal: function() {
            this.$emit("about")
        },
        toggleLegalModal: function() {
            this.$emit('legal')
        }
    }
}
</script>
<style lang="scss" scoped>
    .footer {
        filter: opacity(.5);
        height: 1rem;
        background-color: rgba(0, 0, 0, 0);

        &:hover {
            animation: opacityFade .25s ease-out;
            filter: opacity(1);
        }
    }

    a {
        color: #a9a9a9;
        text-decoration: underline;

        &:hover {
            color: #000;
            transition: all 0.3s ease-in-out;
        }
    }


    @keyframes opacityFade {
        from {
            filter: opacity(.5);
        }
        to {
            filter: opacity(1);
        }
    }
</style>
<!--logo-->
<style lang="scss" scoped>
    path, svg {
        fill: #000 !important;
        color: #000 !important;
        stroke: #000 !important;
    }

    svg {
        height: 1.6rem;
        width: auto;
    }

    .cls-1, .cls-3 {
        fill: #231f20;
    }

    .cls-1 {
        stroke: #231f20;
    }

    .cls-1, .cls-2 {
        stroke-miterlimit: 10;
    }

    .cls-2 {
        fill: #9e1f63;
        stroke: #9e1f63;
    }

    .cls-4 {
        fill: #fff;
    }
</style>