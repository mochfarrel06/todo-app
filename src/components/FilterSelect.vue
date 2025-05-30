<script>
    export default {
        props: {
            modelValue: {
                type: String,
                required: true
            }
        },
        methods: {
            updateValue(value) {
                this.$emit('update:modelValue', value)
            }
        }
    }
</script>

<template>
    <div class="my-4">
        <label class="mr-2">Filter:</label>
        <select :value="modelValue" @input="updateValue($event.target.value)" class="border p-2">
            <option>All</option>
            <option>Work</option>
            <option>Personal</option>
        </select>
    </div>
</template>