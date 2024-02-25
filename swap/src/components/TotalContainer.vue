<template>
    <v-card class="mx-auto" max-width="498" elevation="5">
        <v-img src="../../public/market.svg" height="100px" cover></v-img>

        <v-card-subtitle>
            Total is:
        </v-card-subtitle>

        <v-card-title>
           <h2>{{ totalAmount }} {{ currencySymbol }}</h2>
        </v-card-title>

        <v-card-actions>
            <v-btn color="teal-lighten-1" variant="text" @click="show = !show">
                Show {{ !show ? "rate" : "less" }}
            </v-btn>

            <v-spacer></v-spacer>

            <v-btn :icon="show ? 'mdi-chevron-up' : 'mdi-chevron-down'" @click="show = !show"></v-btn>
        </v-card-actions>

        <v-expand-transition>
            <div v-show="show">
                <v-divider></v-divider>
                <v-card-text>
                    The rate is: {{ rate }}
                </v-card-text>
            </div>
        </v-expand-transition>
    </v-card>
</template>
<script>
export default {
    props: {
        totalAmount: Number,
        currencySymbol: String,
        rate: Number
    },
    data: () => ({
        show: false,
        click: "rate"
    })
}
</script>