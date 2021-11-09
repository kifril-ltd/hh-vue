<template>
    <b-form-group :label="label" :label-for="id" :state="isError" aria-describedby="invalid-message">
        <b-form-invalid-feedback id="invalid-message">
            <ul id="error-messages">
                <!-- <li v-for="error in errors" :key="error.message">
                    {{ error.message }}
                </li> -->
            </ul>
        </b-form-invalid-feedback>
        <b-form-input 
            :id="id" 
            :placeholder="placeholder" 
            :value="value" 
            @input="onInput"
           >
        </b-form-input>
    </b-form-group>
</template>

<script>
    export default {
        name: 'BInput',
        props: {
            id: {
                type: String,
                require: true
            },
            label: {
                type: String,
                require: true
            },
            placeholder: {
                type: String,
                require: false,
                default: ''
            },
            value: {
                type: String,
                require: true,
            },
            rules: {
                type: Array,
                require: false
            },
        },

        data() {
            return {
                isError: true,
                errors: [],
            }
        },

        methods: {
            onInput(event) {
                this.errors = [];

                // for (const rule in this.rules) {
                //     if (!rule.regex.test(inputValue)) {
                //         this.errors.push(rule.message)
                //     }
                // }


                this.$emit('input', event.target.value);
            },

            onChange(event) {
                this.$emit('change', event.target.value);
            },

        },
    }
</script>