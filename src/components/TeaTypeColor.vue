<template>
    <div class="teatypecolor" :style="style">
        
    </div>
</template>
<script>
export default {
    name: 'TeaTypeColor',
    props: ['type'],
    computed: {
        color: function() {
            switch (this.type) {
                case 'white': return "#F5F5F5";
                case 'black': return "#B53737";
                case 'yellow': return "#FADA5E";
                case 'oolong': return "#FFAA1D";
                case 'green': return "#54B948";
                default:
                    break;
            }
            return null;
        },
        style: function() {
            return {
                background: this.color
            }
        }
    }
}
</script>
<style lang="scss" scoped>
    .teatypecolor {
        width: 1.3rem;
        height: 1.3rem;
        border-radius: 50%;
        border: 2px #000 solid;
        margin-right: .3rem;
    }
</style>