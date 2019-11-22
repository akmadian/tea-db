<template>
    <div id="brewingparams">
        <div class="columns">
            <div class="column is-one-fifth">
                <b>Water Temp</b><br>
                <span>
                    <font-awesome-icon icon="thermometer-three-quarters"></font-awesome-icon>
                    {{data.gongfu.temp}}&deg;
                    <!--
                    <p v-if="data.gongfu.tempUnitisFarenheit">F</p>
                    <p v-else>C</p>-->
                </span>
            </div>
            <div class="column is-one-fifth">
                <b>Amount</b>
                <p class="help">g per 100ml</p>
                <p>
                    {{data.gongfu.gper100ml}}
                </p>
            </div>
            <div class="column is-one-fifth">
                <b>1st Infusion</b>
                <p class="help">seconds</p>
                <p>
                    {{data.gongfu.infusiontimes.first}}
                </p>
            </div>
            <div class="column is-one-fifth">
                <b>+ Infusions</b>
                <p class="help">seconds</p>
                <p>
                    {{data.gongfu.infusiontimes.next}}
                </p>
            </div>
            <div class="column is-one-fifth">
                <b>Number of Infusions</b>
                <p>
                    {{data.gongfu.numinfusions}}
                </p>
            </div>
        </div>
    </div>
</template>
<script>
import { library } from '@fortawesome/fontawesome-svg-core'
import { faThermometerThreeQuarters } from '@fortawesome/free-solid-svg-icons'

library.add(faThermometerThreeQuarters)

export default {
    name: 'BrewingParams',
    props: ['data'],

}
</script>
<style lang="scss" scoped>
    #brewingparams {
        width: 60%;
    }

    .help {
        margin-top: 0rem;
    }
</style>