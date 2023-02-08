<template>
    <ul>
        <li v-for="(chip, i) in cartData" :key="chip.title">
            <strong>{{ chip.title }}</strong> <span>{{ chip.price }}원</span>
            <button @click="deleteCart(i)">삭제</button>
        </li>
    </ul>
</template>

<script>
export default {
    emits: [
        'delete-item',
    ],
    props: {
        cartData: Array,
    },
    methods: {
        deleteCart(idx) {
            this.$emit('delete-item', idx);
        },
    },
}
</script>

<style>

</style>