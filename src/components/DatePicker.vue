<script>
import DatePicker from 'vue2-datepicker';
import 'vue2-datepicker/index.css';

export default {
    components: { DatePicker },
    data() {
        return {
            time1: null,
            range: null
        };
    },
    methods: {
        getRange(range) {
            this.$emit('get-range', range);
        }
    },
    emits: ['get-range']
};
</script>
    
<template>
    <div>
        <div>
            <h1>Pick a date</h1>
            <date-picker v-model="time1" valueType="timestamp"></date-picker>
            <div v-if="time1 != null">
                <p>The day you chose was {{time1}}</p>

                <div>In lunar calendar, the date is 
                    <lunar-calendar>

                    </lunar-calendar>
                </div>

            </div>
        </div>
        <div>
            <h1>Pick a date range</h1>
            <date-picker v-model="range" range valueType="timestamp" @change="getRange(range)" ></date-picker>

        </div>
    </div>
</template>
    
<style scoped>

</style>
    