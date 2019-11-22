<template>
    <div>
        <button class="button is-primary is-medium"
            @click="isComponentModalActive = true">
            Launch component modal
        </button>
        <b-table :data="importData" :columns="columns">
            <template slot-scope="props">
                <b-table-column field="name">
                    {{ props.row.name }}
                </b-table-column>
                <b-table-column field="rating" numeric sortable>
                    {{ props.row.rating }}
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
                    <div class="content">
                        <h1 class="title">Add New Tea</h1>
                        <b-field label="Name">
                            <b-input :value="Name"></b-input>
                        </b-field>
                        <b-field label="Rating">
                            <b-numberinput min="0" max="10"></b-numberinput>
                        </b-field>
                        <b-field label="Type">
                            <b-select placeholder="Select Type">
                                <option value="white">White</option>
                                <option value="black">Black</option>
                                <option value="yellow">Yellow</option>
                                <option value="puerh">Pu Erh</option>
                                <option value="green">Green</option>
                                <option value="oolong">Oolong</option>
                            </b-select>
                        </b-field>
                    </div>
                </div>
            </div>
        </b-modal>
    </div>
</template>

<script>
    import TeaTypeColor from './TeaTypeColor.vue'

    export default {
        components: {
            TeaTypeColor
        },
        data() {
            return {
                importData: require('../test.json'),
                isPaginated: true,
                sortIcon: 'arrow-up',
                sortIconSize: 'is-small',
                isComponentModalActive: false,
                formProps: {
                    email: 'evan@you.com',
                    password: 'testing'
                },
                newTea: {
                    "name": "",
                    "rating": 0,
                    "type": ""
                },
                columns: [
                    {
                        field: 'name',
                        label: 'Name',
                        searchable: true
                    },
                    {
                        field: 'rating',
                        label: 'Rating',
                        numeric: true
                    },
                    {
                        field: 'type',
                        label: 'Type',
                        searchable: true
                    },
                    {
                        field: 'harvest',
                        label: 'Harvest'
                    }
                ]
            }
        },
        methods: {
            add: function(obj) {
                this.importData.push(obj)
            }
        }
    }
</script>
<style lang="scss" scoped>
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