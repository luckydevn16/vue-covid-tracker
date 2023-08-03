<template>
    <div class="country-select-container">
        <select v-model="selected" @change="countrySelectMethod()" class="country-select">
            <option value="0">Select Country</option>
            <option v-for="country in countries" :key="country.ID" :value="country.ID">
                {{ country.Country }}
            </option>
        </select>
    </div>
</template>

<script>

export default {
    name: 'CountrySelect',
    props: ['countries'],
    data() {
        return {
            selected: 0
        }
    },
    methods: {
        countrySelectMethod() {
            const country = this.countries.find((item) => item.ID === this.selected);

            this.$emit('getCountry', country);
        }
    }
}
</script>

<style>
.country-select {
    width: 100%;
    max-width: 300px;
    height: 40px;
    padding: 8px;
    font-size: 1rem;
    color: #555;
    outline: none;
    border: 1px solid #ccc;
    border-radius: 4px;
}
.country-select:focus {
    border: 2px solid #145DBF;
}
.country-select option {
    background-color: rgba(0,0,0,.7);
    color: #eee;
}
</style>
