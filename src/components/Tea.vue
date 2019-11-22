<template>
    <div class="columns" id="tea">
        <div class="column is-four-fifths">
            <h1 class="title is-1">{{data.name}}</h1>
            <hr>
            <h5 class="subtitle is-5">Notes</h5>
            {{data.notes}}
            <BrewingParams :data="data.brewingparams"></BrewingParams>
        </div>
        <div class="column" id="details-col">
            <h4 class="subtitle is-4">Details</h4>
            <div class="tea-detail">
                <span class="left"><b>Type</b></span>
                <span class="right">{{data.type}}<TeaTypeColor :type="data.type"/></span>
            </div><br>
            <div class="tea-detail">
                <span class="left"><b>Harvest</b></span>
                <span class="right">{{data.harvest}}</span>
            </div><br>
            <div class="tea-detail">
                <span class="left"><b>Price/ Gram</b></span>
                <span class="right">${{data.ppg}}</span>
            </div><br>
            <div class="tea-detail">
                <span class="left"><b>g/ 100ml</b></span>
                <span class="right">{{data.brewingparams.gongfu.gper100ml}}g</span><br>
                <div class="indent">
                    <b-field label="Convert to Other Vessel Sizes">
                        <b-input placeholder="140"></b-input>
                    </b-field>
                </div>
            </div>
        </div>
    </div>
</template>
<script>
import TeaTypeColor from './TeaTypeColor.vue'
import BrewingParams from './BrewingParams.vue'

export default {
    name: 'tea',
    props: ['data'],
    components: {
        TeaTypeColor,
        BrewingParams
    },
    data() {
        return {
            info: {
                "name": "test white",
                "rating": 9,
                "type": "white",
                "harvest": "Spring 2019",
                "id": 1,
                "ppg": .56,
                "notes": "ajshbfjlhakshfeawjhflawejhgalkwjerhgalwkejrhgalekjfhdsalkjhfaslke",
                "brewingparams": {
                    "gongfu": {
                        "temp": 200,
                        "tempUnitisFarenheit": true,
                        "numinfusions": 12,
                        "infusiontimes": {
                            "first": 20,
                            "next": 5
                        },
                        "gper100ml": 5
                    }
                }
            }
        }
    }
}
</script>
<style lang="scss" scoped>
    #details-col {
        margin-right: 1rem;
    }

    #tea {
        height: 100%;
    }

    .indent {
        margin-left: 1rem;
    }

    input {
        width: 5rem;
    }

    .tea-detail {
        display: block;
        margin-top: 1rem;

        .left {
            float: left
        }
        .right {
            float: right;
        }

        .teatypecolor {
            display: inline-block;
            margin-left: .5rem;
        }
    }
</style>