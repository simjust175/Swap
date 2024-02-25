<template>
    <v-sheet width="500" class="mx-auto mt-8 pa-8 rounded" elevation="12">
        <v-form fast-fail @submit.prevent width="300">
            <v-div class="currency1"> <v-text-field v-model="amount" label="Enter currency amount" :rules="currencyRules">
                </v-text-field>
                <select-currency order="currency1" class="small-select" v-bind="$attrs"/>
            </v-div>

            <select-currency order="currency2" id="large-select" v-bind="$attrs" />


            <v-btn type="submit" block class="get-rate-btn" height="50" width="100%" :loading="loading" :disabled="disabled" color="secondary"
                @click="emitGetRate">Get rate <span v-if="currency2"> in {{ currency2 }}</span></v-btn>
        </v-form>
    </v-sheet>
</template>
<script>

export default {
    props:{ currency2: String },

    data: () => ({
        loader: null,
        loading: false,
        disabled: true,
        amount: "",
        currencyRules: [
            value => {
                if (!Number(value)) return 'Enter a valid amount'
            },
        ],
    }),
    methods: {
        emitGetRate() {
            console.log("amount", Number(this.amount));
            this.loader = 'loading';
            this.$emit("get-initialized", this.amount)
        }
    },
    watch: {
        amount() {
            this.disabled = Number(this.amount) ? false : true;
        },
        loader() {
            const l = this.loader
            this[l] = !this[l]

            setTimeout(() => (this[l] = false), 2000)
            this.loader = null
        },
    },
}
</script>
  
<style>
.small-select  {
    width: 15px;
}

.custom-loader {
    animation: loader 1s infinite;
    display: flex;
}

.currency1 {
    display: flex;
}

.get-rate-btn{
    margin: 0;
    margin-right: 32px;
}

@-moz-keyframes loader {
    from {
        transform: rotate(0);
    }

    to {
        transform: rotate(360deg);
    }
}

@-webkit-keyframes loader {
    from {
        transform: rotate(0);
    }

    to {
        transform: rotate(360deg);
    }
}

@-o-keyframes loader {
    from {
        transform: rotate(0);
    }

    to {
        transform: rotate(360deg);
    }
}

@keyframes loader {
    from {
        transform: rotate(0);
    }

    to {
        transform: rotate(360deg);
    }
}

.custom-loader {
    animation: loader 1s infinite;
    display: flex;
}

@-moz-keyframes loader {
    from {
        transform: rotate(0);
    }

    to {
        transform: rotate(360deg);
    }
}

@-webkit-keyframes loader {
    from {
        transform: rotate(0);
    }

    to {
        transform: rotate(360deg);
    }
}

@-o-keyframes loader {
    from {
        transform: rotate(0);
    }

    to {
        transform: rotate(360deg);
    }
}

@keyframes loader {
    from {
        transform: rotate(0);
    }

    to {
        transform: rotate(360deg);
    }
}
</style>