<template>
    <button @click="onClick" class="btn">{{text}}</button>
</template>

<script>

export default {
    name: 'TheButton',
    props: ['text'],
    methods: {
        onClick(){
            this.$emit('btn-click');
        }
    }
}
</script>
<style scoped>
.btn {
  margin-top: -36px;
  margin-left: 10px;
  padding: 15px 20px;
  background-color: black;
  color: white;
  border: 2px solid black;
  border-radius: 5px;
  font-size: 15pt;
  cursor: pointer;
}
.btn:hover {
  background-color: #535353;
  border: 2px solid #535353;
}
.btn:active {
  background-color: #797979;
  border: 2px solid #797979;
}
</style>