<script>
import { Bar, Line } from 'vue-chartjs/legacy'
import * as moment from 'moment'

export default {
    props: {
        range: {
            type: Array
        }
    },
    components: {
        Bar, Line
    },
    watch: {
        range: {
            immediate: true,
            deep: true,
            handler() {
                let start = this.$props.range[0];
                let end = this.$props.range[1];
                let sampleSet = this.$data.sample;
                let availableStart = sampleSet[0].time;
                let availableEnd = sampleSet[sampleSet.length - 1].time;
                if (end < availableStart || start > availableEnd) {
                    this.$data.labels = null;
                    this.$data.dataset1 = null;
                    this.$data.dataset2 = null;
                    this.$data.chartData1 = null;
                    this.$data.chartData2 = null;
                } else {
                    if (start <= availableStart) {
                        start = availableStart;
                    }
                    if (end >= availableEnd) {
                        end = availableEnd;
                    }
                    let labelSet = [];
                    let newSet1 = [];
                    let newSet2 = [];
                    sampleSet.every(function (ele, index) {
                        if (ele.time > end) {
                            return false;
                        }
                        if (ele.time >= start && ele.time <= end) {
                            labelSet.push(ele.label);
                            newSet1.push(ele.dataset1);
                            newSet2.push(ele.dataset2);
                        }
                        return true;
                    })
                    this.$data.labels = labelSet;
                    this.$data.dataset1 = newSet1;
                    this.$data.dataset2 = newSet2;
                    this.$data.chartData1 = {
                        labels: labelSet,
                        datasets: newSet1
                    }
                    this.$data.chartData2 = {
                        labels: labelSet,
                        datasets: newSet2
                    }
                }
            }
        }
    },
    data() {
        return {
            labels: null,
            dataset1: null,
            dataset2: null,
            chartOptions: {
                responsive: true,
            },
            chartData1: null,
            chartData2: null,
            sample:
                [
                    {
                        "time": 1662310800000,
                        "label": "05/09",
                        "dataset1": 24,
                        "dataset2": 10
                    },
                    {
                        "time": 1662397200000,
                        "label": "06/09",
                        "dataset1": 79,
                        "dataset2": 14
                    },
                    {
                        "time": 1662483600000,
                        "label": "07/09",
                        "dataset1": 53,
                        "dataset2": 87
                    },
                    {
                        "time": 1662570000000,
                        "label": "08/09",
                        "dataset1": 20,
                        "dataset2": 18
                    },
                    {
                        "time": 1662656400000,
                        "label": "09/09",
                        "dataset1": 41,
                        "dataset2": 36
                    },
                    {
                        "time": 1662742800000,
                        "label": "10/09",
                        "dataset1": 24,
                        "dataset2": 86
                    },
                    {
                        "time": 1662829200000,
                        "label": "11/09",
                        "dataset1": 26,
                        "dataset2": 28
                    },
                    {
                        "time": 1662915600000,
                        "label": "12/09",
                        "dataset1": 28,
                        "dataset2": 83
                    },
                    {
                        "time": 1663002000000,
                        "label": "13/09",
                        "dataset1": 90,
                        "dataset2": 68
                    },
                    {
                        "time": 1663088400000,
                        "label": "14/09",
                        "dataset1": 7,
                        "dataset2": 29
                    },
                    {
                        "time": 1663174800000,
                        "label": "15/09",
                        "dataset1": 0,
                        "dataset2": 67
                    },
                    {
                        "time": 1663261200000,
                        "label": "16/09",
                        "dataset1": 82,
                        "dataset2": 99
                    },
                    {
                        "time": 1663347600000,
                        "label": "17/09",
                        "dataset1": 41,
                        "dataset2": 42
                    },
                    {
                        "time": 1663434000000,
                        "label": "18/09",
                        "dataset1": 24,
                        "dataset2": 38
                    },
                    {
                        "time": 1663520400000,
                        "label": "19/09",
                        "dataset1": 15,
                        "dataset2": 88
                    },
                    {
                        "time": 1663606800000,
                        "label": "20/09",
                        "dataset1": 48,
                        "dataset2": 93
                    },
                    {
                        "time": 1663693200000,
                        "label": "21/09",
                        "dataset1": 71,
                        "dataset2": 96
                    },
                    {
                        "time": 1663779600000,
                        "label": "22/09",
                        "dataset1": 34,
                        "dataset2": 96
                    },
                    {
                        "time": 1663866000000,
                        "label": "23/09",
                        "dataset1": 1,
                        "dataset2": 69
                    },
                    {
                        "time": 1663952400000,
                        "label": "24/09",
                        "dataset1": 89,
                        "dataset2": 28
                    },
                    {
                        "time": 1664038800000,
                        "label": "25/09",
                        "dataset1": 60,
                        "dataset2": 71
                    },
                    {
                        "time": 1664125200000,
                        "label": "26/09",
                        "dataset1": 34,
                        "dataset2": 99
                    },
                    {
                        "time": 1664211600000,
                        "label": "27/09",
                        "dataset1": 20,
                        "dataset2": 2
                    },
                    {
                        "time": 1664298000000,
                        "label": "28/09",
                        "dataset1": 24,
                        "dataset2": 23
                    },
                    {
                        "time": 1664384400000,
                        "label": "29/09",
                        "dataset1": 6,
                        "dataset2": 38
                    },
                    {
                        "time": 1664470800000,
                        "label": "30/09",
                        "dataset1": 89,
                        "dataset2": 3
                    },
                    {
                        "time": 1664557200000,
                        "label": "01/10",
                        "dataset1": 11,
                        "dataset2": 48
                    },
                    {
                        "time": 1664643600000,
                        "label": "02/10",
                        "dataset1": 86,
                        "dataset2": 68
                    },
                    {
                        "time": 1664730000000,
                        "label": "03/10",
                        "dataset1": 92,
                        "dataset2": 58
                    },
                    {
                        "time": 1664816400000,
                        "label": "04/10",
                        "dataset1": 82,
                        "dataset2": 72
                    },
                    {
                        "time": 1664902800000,
                        "label": "05/10",
                        "dataset1": 78,
                        "dataset2": 68
                    }
                ]
        }
    }
}
</script>

<template>
    <div>
        <div v-if="this.$props.range[0] != null && this.$props.range[1] != null">
            The time range is: {{ this.$props.range[0] }} to {{this.$props.range[1]}}
        </div>

        <div>
            <div v-if="labels != null && labels.length > 0">
                <!-- <Bar :chart-options="chartOptions" :chart-data="chartData1" /> -->

                <!-- <Bar :chart-options="chartOptions" :chart-data="chartData1" :chart-id="'chartId'"
                    :dataset-id-key="'label'" /> -->
                <div v-for="(label, index) in labels" :key="index">
                    <p>{{label}}: {{dataset1[index]}} | {{dataset2[index]}}</p>
                </div>
                <!-- <line :chart-options="chartOptions" :chart-data="chartData2">

                </line> -->
            </div>
            <div v-else>
                There is no data in this range
            </div>
        </div>
    </div>
</template>