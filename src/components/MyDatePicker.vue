<script>
import DatePicker from 'vue2-datepicker';
import 'vue2-datepicker/index.css';
import { LunarDate } from 'vietnamese-lunar-calendar';

export default {
    components: { DatePicker, LunarDate },
    data() {
        return {
            time1: null,
            lunarTime: null,
            range: null
        };
    },
    methods: {
        getRange(range) {
            this.$emit('get-range', range);
        },

        getLunarDate(date) {
            if (date != null)
                this.$data.lunarTime = new LunarDate(new Date(this.$data.time1));
        }
    },
    emits: ['get-range']
};
</script>
    
<template>
    <div>
        <div>
            <h1>Pick a date</h1>
            <date-picker v-model="time1" format="DD-MM-YYYY" valueType="timestamp" @change="getLunarDate(time1)">
            </date-picker>

            <div v-if="time1 != null">

                <div>
                    The lunar date is
                    {{lunarTime.getDate()}}/{{lunarTime.getMonth()}}/{{lunarTime.getYear()}}
                </div>

            </div>
        </div>
        <div>
            <h1>Pick a date range</h1>
            <date-picker v-model="range" range valueType="timestamp" @change="getRange(range)" format="DD-MM-YYYY">
            </date-picker>

        </div>
    </div>
</template>
    
<style scoped>

</style>
    