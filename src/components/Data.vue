<template>
    <div>
        <div v-for="child in Object.entries(objectValues)" :key="child[1]">
            <Display :title="child[0].split('_')[0]" :value="child[1]" :options="child[0].split('_')[1]" :isEdit="isEdit"/>
        </div>
    </div>
</template>

<script>
import Display from '../components/Display'
export default {
    data: function () {
        return {
            isEdit: true,
            objectValues: {}
        }
    },
    components: {
        Display
    },
    props: {
        object: Object
    },
    methods: {
        checkData: function () {
            console.log(this.object);
            console.log(this.objectValues)
            this.objectValues = {...this.object}
            console.log(Object.entries(this.objectValues));
        }
    },
    mounted() {
        this.checkData()
    }
}
</script>