<template>
<div class="hello">
    <div id="checkout-button" class="onepipe-checkout" :amount="amount" :class="[ 'onepipe-checkout', 'onepipe-checkout--'+size, {'onepipe-checkout--rounded' : rounded}  ]" @click.prevent="checkout">
        <slot></slot>
    </div>
</div>
</template>

<script>
/* eslint-disable */

export default {
    name: 'Checkout',
    props: {
        size: {
            type: String,
            default: "default",
            validator(x) {
                return ["sm", "md", "lg"].indexOf(x) !== -1;
            },
        },

        rounded: {
            type: Boolean,
            default: true
        },
        request_type: {
            type: String
        },
        api_key: {
            type: String
        },
        customer: {
            type: Object,
        },
        options: {
            type: Object,
        },
        meta: {
            type: Object,
        },
        details: {
            type: Object,
        },
        amount: {
            type: Number,
        },
        transaction_ref: {
            type: String,
        },
        transaction_parent_ref: {
            type: String,
        },
        transaction_desc: {
            type: String,
        },
        callback: {
            type: Function,
            required: true,
            default: function (response) {}
        },
        close: {
            type: Function,
            required: true,
            default: function () {}
        },
    },
    created() {
        this.btnSize = this.size;
        this.scriptLoaded = new Promise((resolve) => {
            this.loadOnepipe(() => {
                resolve()
            })
        });
    },
    data() {
        return {
            btnSize: 'md',
            scriptLoaded: null
        }
    },
    methods: {
        loadOnepipe(callback) {
            const script = document.createElement('script')
            script.src = 'https://js.dev.onepipe.io/v2'
            document.getElementsByTagName('head')[0].appendChild(script)
            if (script.readyState) { // IE
                script.onreadystatechange = () => {
                    if (script.readyState === 'loaded' || script.readyState === 'complete') {
                        script.onreadystatechange = null
                        callback()
                    }
                }
            } else { // Others
                script.onload = () => {
                    callback()
                }
            }
        },
        checkout() {
            this.scriptLoaded && this.scriptLoaded.then(() => {
                let requestData = {
                    request_ref: Math.floor((Math.random() * 1434)) + '78805' + Math.floor((Math.random() * 4543)), //generate a unique number
                    request_type: this.request_type,
                    api_key: this.api_key,
                    auth: null,
                    transaction: {
                        // mock_mode: 'inspect',
                        transaction_ref: this.transaction_ref || Math.floor((Math.random() * 1434)) + '78805' + Math.floor((Math.random() * 4543)), //generate a unique number
                        transaction_desc: this.description || '',
                        transaction_ref_parent: "",
                        amount: this.amount, // in kobo
                        customer: this.customer,
                        // options: null,
                        options: this.options,
                        details: null
                    }
                };

                if (this.mock_mode) {
                    requestData.transaction.mock_mode = this.mock_mode
                }

                console.log(requestData);

                if (typeof OnePipePopup != "undefined") {
                    let handler = OnePipePopup.setup({
                        requestData,
                        callback: (response) => {
                            this.callback(response)
                        },
                        onClose: () => {
                            alert('You cancelled the payment process');
                        }
                    });
                    handler.execute();
                }

            });
        },

    }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->

<style scoped>
.onepipe-checkout {
    font-size: 18px;
    background-color: #0e9bb9;
    color: #ffffff;
    display: inline-block;
    outline: 0;
    border: 1px solid rgba(0, 0, 0, 0.1);
    font-weight: 500;
    font-family: "Helvetica Neue", Helvetica, Arial, sans-serif;
    user-select: none;
    cursor: pointer;
}

/* --> SIZES <-- */

.onepipe-checkout--sm {
    padding: 8px 10px;
    border-radius: 4px;
    font-size: 12px;
    line-height: 12px;
}

.onepipe-checkout--md {
    padding: 12px 14px;
    border-radius: 6px;
    font-size: 14px;
    line-height: 16px;
}

.onepipe-checkout--lg {
    padding: 16px 18px;
    border-radius: 8px;
    font-size: 16px;
    line-height: 20px;
}

/* --> BOOLEANS <-- */

.onepipe-checkout--rounded {
    border-radius: 60px;
}
</style>
