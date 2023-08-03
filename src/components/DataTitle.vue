<template>
    <div class="data-title-container">
        <h2 class="data-title">{{text}}</h2>
        <div class="data-date">
            {{timestamp}}
        </div>
    </div>
</template>

<script>
import moment from 'moment';

export default {
    name: 'DataTitle',
    props: ['text', 'dataDate'],
    computed: {
        timestamp: function() {
            return moment(this.dataDate).format('MMMM Do YYYY, h:mm:ss a')
        }
    }
}
</script>

<style>
.data-title-container, .data-title {
    text-align: center;
}
.data-title {
    color: #145DBF;
    margin-bottom: 0.5rem;
    font-weight: 300;
    font-size: 2.2rem;
}
.data-date {
    font-size: 0.9rem;
    opacity: .7;
}
</style>
