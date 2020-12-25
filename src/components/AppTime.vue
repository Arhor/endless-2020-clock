<template>
    <div class="numbers-small">
        <app-number :value="hours" small />
        <span class="colon">:</span>
        <app-number :value="minutes" small />
        <span class="colon">:</span>
        <app-number :value="seconds" small />
    </div>
</template>

<script>
import AppNumber from '@/components/AppNumber.vue';

export default {
    name: 'AppTime',
    components: {
        AppNumber,
    },
    props: {
        hours: String,
        minutes: String,
        seconds: String,
    },
};
</script>
