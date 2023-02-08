<template>
    <ul class="list">
        <li v-for="(chip, i) in chipsData" :key="chip.title">
            <img :src="require(`@/assets/${chip.img}`)" />
            <strong>{{ chip.title }}</strong>
            <span>{{ chip.desc }}</span>
            <b>{{ chip.price }}원</b>
            <button @click="add(i)">add item</button>
        </li>
    </ul>
</template>

<script>
export default {
    props: {
        chipsData: Array,
    },
    methods: {
        add(idx) {
            this.$emit('add-item', idx);
        },
    },
}
</script>

<style>

</style>