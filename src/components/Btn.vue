<script>
 export default {
    props: {
        variation: String
    }
 }
</script>

<template>
  <button :class="['btn', `btn-${variation}`]" @click="click"><slot></slot></button>
</template>

<style>
.btn{
    background-color: red;
    border: none;
    color: white;
    padding: 5px 20px;
    font-size: 2.3rem;
    height: 50px;
    border-radius: 8px;
    cursor: pointer;
    transition: 0.2s all;
}
.btn:hover{
    background-color: rgb(194, 11, 11);
}
</style>