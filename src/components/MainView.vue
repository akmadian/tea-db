<template>
    <div ref="cont">
        <Tea 
            :data="selectedTea" 
            ref="activeTea"
            v-if="teaComponentActive">
        </Tea>
        <StashTable 
            :data="allTeas"
            ref="stashTable"
            @newSelection="setSelectedTea"
            v-else>
        </StashTable>
    </div>
</template>
<script>
import Tea from './Tea.vue'
import StashTable from './StashTable.vue'

var data = require('../test.json')

export default {
    name: 'MainView',
    props: ['isTeaComponentActive'],
    components: {
        Tea,
        StashTable
    },
    data: function() {
        return {
            allTeas: data,
            teaComponentActive: this.isTeaComponentActive,
            dynamicComponent: StashTable,
            selectedTea: data[0]
        }
    },
    methods: {
        swap: function() {
            this.dynamicComponent = StashTable
        },
        setSelectedTea(payload) {
            this.$emit('newSelected')
            this.selectedTea = payload
            this.teaComponentActive = true
        }
    },
    created() {
        window.addEventListener('keydown', (e) => {
            if (e.key == 'Escape') {
                if (this.teaComponentActive) {
                    this.teaComponentActive = false
                }
            }
        })
    }
}
</script>