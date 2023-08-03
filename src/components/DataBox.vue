<template>
<div class="data-box">
    <div class="data-box-card cases-card">
        <h3 class="data-box-heading">Cases</h3>
        <p class="data-box-text">
            <b>Today: </b> {{ numberWithCommas(stats.NewConfirmed) }}
        </p>
        <p class="data-box-text">
            <b>Total: </b> {{ numberWithCommas(stats.TotalConfirmed) }}
        </p>
    </div>
    <div class="data-box-card deaths-card">
        <h3 class="data-box-heading">Deaths</h3>
        <p class="data-box-text">
            <b>Today: </b> {{ numberWithCommas(stats.NewDeaths) }}
        </p>
        <p class="data-box-text">
            <b>Total: </b> {{ numberWithCommas(stats.TotalDeaths) }}
        </p>
    </div>
</div>
</template>

<script>

export default {
    name: 'DataBox',
    props: ['stats'],
    methods: {
        numberWithCommas(x) {
            return x.toString().replace(/\B(?=(\d{3})+(?!\d))/g, ',');
        }
    }
}
</script>

<style>
.data-box {
    display: flex;
    flex-wrap: wrap;
    justify-content: center;
    align-items: center;
}
.data-box-card {
    width: 100%;
    max-width: 300px;
    margin: 0 auto;
    padding: 2rem 1rem;
    display: grid;
    place-items: center center;
    border-radius: 4px;
    margin: 1rem .5rem 0 .5rem;
    line-height: 150%;
    box-shadow: 0 3px 12px #bbb;
}
.cases-card {
    background-color: #FFC107;
    color: #444
}
.deaths-card {
    background-color: #DC3545;
    color: #ddd
}
.data-box-heading {
    font-weight: 300;
    font-size: 1.5rem;
    margin-bottom: 0.7rem;
}
.data-box-text {
    font-size: 0.9rem;
}
</style>
