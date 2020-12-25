<template>
    <div class="numbers">
        <app-number :value="day" />
        <span class="colon">-</span>
        <app-number :value="month" />
        <span class="colon">-</span>
        <app-number :value="year" />
    </div>
</template>

<script>
import AppNumber from '@/components/AppNumber.vue';

export default {
    name: 'AppDate',
    components: {
        AppNumber,
    },
    props: {
        day: String,
        month: String,
        year: String,
    },
};
</script>
