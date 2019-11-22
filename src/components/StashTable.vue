<template>
    <div id="stashtable">
        <div>
            <h1 class="title is-1" style="float: left">My Stash</h1>
            <button 
                class="button is-primary" 
                style="float: right"
                @click="isComponentModalActive = true">
                Add New
            </button>
        </div>
        <b-table 
            :data="importData" 
            :columns="columns"
            @select="emitNewSelection">
            <template slot-scope="props">
                <b-table-column 
                    field="name"
                    style="cursor: pointer">
                    {{ props.row.name }}
                </b-table-column>
                <b-table-column field="rating" numeric sortable>
                    {{ props.row.rating }}
                </b-table-column>
                <b-table-column field="ppg" numeric sortable>
                    ${{ props.row.ppg / 100 }}
                </b-table-column>
                <b-table-column field="type" sortable>
                    <div class="columns pad-top">
                        <TeaTypeColor 
                            :name="props.row.id" 
                            :type="props.row.type"/>
                        {{ props.row.type }}
                    </div>
                </b-table-column>
                <b-table-column field="harvest" sortable>
                    {{ props.row.harvest }}
                </b-table-column>
            </template>
        </b-table>
        <b-modal :active.sync="isComponentModalActive">
            <div class="card">
                <div class="card-content">
                    <div 
                        class="content"
                        style="width: 80%; margin: 0 auto;">
                        <h1 class="title">Add New Tea</h1>
                        <b-field label="Name">
                            <b-input :value="Name" v-model="newTea.name"></b-input>
                        </b-field>
                        <b-field label="Rating">
                            <b-numberinput min="0" max="10" v-model="newTea.type"></b-numberinput>
                        </b-field>
                        <b-field label="Type">
                            <b-select placeholder="Select Type" v-model="newTea.type">
                                <option value="white">White</option>
                                <option value="black">Black</option>
                                <option value="yellow">Yellow</option>
                                <option value="puerh">Pu Erh</option>
                                <option value="green">Green</option>
                                <option value="oolong">Oolong</option>
                            </b-select>
                        </b-field>
                        <div class="columns">
                            <div class="column">
                                <label for=""><b>Price</b></label>
                                <b-field class="has-addons">
                                    <b-input placeholder="X" v-model="newTea.price"></b-input>
                                    <b-select v-model="newTea.currency" placeholder="$">
                                        <option value="usd">$</option>
                                        <option value="gbp">&pound;</option>
                                        <option value="eur">&euro;</option>
                                        <option value="cny">&yen;</option>
                                    </b-select>
                                </b-field>
                            </div>
                            <div class="column">
                                <label for=""><b>Amount Purchased</b></label>
                                <b-field class="has-addons">
                                    <b-input placeholder="X" v-model="newTea.weight"></b-input>
                                    <b-select v-model="newTea.weightUnits" placeholder="g">
                                        <option value="gram">g</option>
                                        <option value="kilo">kg</option>
                                        <option value="ounce">oz</option>
                                        <option value="pound">lb</option>
                                    </b-select>
                                </b-field>
                            </div>
                        </div>
                        <div>
                            <b-button
                                style="margin-right: 1rem"
                                @click="addNewTea">
                                Submit
                            </b-button>
                            <b-button 
                                type="is-danger">
                                Cancel
                            </b-button>
                        </div>
                    </div>
                </div>
            </div>
        </b-modal>
    </div>
</template>

<script>
    import TeaTypeColor from './TeaTypeColor.vue'

    export default {
        name: 'StashTable',
        props: ['data'],
        components: {
            TeaTypeColor
        },
        data() {
            return {
                importData: this.data,
                isPaginated: true,
                sortIcon: 'arrow-up',
                sortIconSize: 'is-small',
                isComponentModalActive: false,
                newTea: {
                    "name": "",
                    "rating": 0,
                    "type": "Select Type",
                    "weightUnits": "g",
                    "weight": "",
                    "price": "",
                    "currency": "$"
                },
                columns: [
                    {
                        field: 'name',
                        label: 'Name'
                    },
                    {
                        field: 'rating',
                        label: 'Rating',
                        numeric: true
                    },
                    {
                        field: 'ppg',
                        label: '$/ gram',
                        numeric: true
                    },
                    {
                        field: 'type',
                        label: 'Type'
                    },
                    {
                        field: 'harvest',
                        label: 'Harvest'
                    }
                ]
            }
        },
        methods: {
            addNewTea: function() {
                this.importData.push(this.newTea)
                this.isComponentModalActive = false
                this.newTea = {
                    "name": "",
                    "rating": 0,
                    "type": "Select Type",
                    "weightUnits": "g",
                    "weight": "",
                    "price": "",
                    "currency": "$"
                }
            },
            emitNewSelection(payload) {
                this.$emit('newSelection', payload)
            }
        }
    }
</script>
<style lang="scss" scoped>
    #stashtable {
        margin-top: 2rem;
        margin-right: 2rem;
    }

    .typecircle {
        background: #f00;
        width: 1.3rem;
        height: 1.3rem;
        border-radius: 50%;
        vertical-align: middle;
        margin-right: .5rem;
    }

    .pad-top {
        margin-top: 0rem;
    }
</style>