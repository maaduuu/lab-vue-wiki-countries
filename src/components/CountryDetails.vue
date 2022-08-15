<template>

<div class="col-7">
        <img
            :src="`https://flagpedia.net/data/flags/icon/72x54/${item.alpha2Code.toLowerCase()}.png`"
            alt="country flag"
            style="width: 300px"
        />
        <h1>
            {{ item.name.common }}
        </h1>
        <table class="table">
            <thead></thead>
            <tbody>
                <tr>
                    <td style="width: 30%">Capital</td>
                    <!-- <td>Paris</td> -->
                    <td>{{ item.capital[0] }}</td>
                </tr>
                <tr>
                    <!-- <td>Area</td>
                    <td>551695 km <sup>2</sup></td> -->
                    <td>Area</td>
                    <td>{{ item.area }} km <sup>2</sup></td>
                </tr>
                <tr>
                    <td>Borders</td>
                    <td>
                        <ul  v-for="(items,idx) in this.item.borders" :key="idx">
                            <a :href="`${items}`"><li class="list-unstyled">{{items}}</li></a>
                        </ul>

                        <!-- <ul v-for="(item, idx) in this.item" :key="idx">
                            <li>
                                <a href="/AND">{{ item }}</a>
                            </li>
                        </ul> -->
                    </td>
                </tr>
            </tbody>
        </table>
    </div>

</template>

<script>
import Countries from "../../public/countries.json";

export default {
    name: "CountryDetails",
    data() {
        return {
            countries: Countries,

            item: Countries.filter(
                (e) => e.alpha3Code === this.$route.params.id
            )[0],
        };
    },
};
</script>

<style>

</style>