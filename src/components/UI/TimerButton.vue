<template>
  <button>
<slot></slot>
  </button>
</template>

<script>
export default {

}
</script>

<style  scoped>
button {
  cursor: pointer;
  width: 20%;
  height: 60px;
  color: white;
  background: 0;
  border: 2px solid white;
  border-radius: 20px;
  margin: 10px;
  transition: 0.5s ease-in-out;
}
button:hover {
  color: ;
}
</style>
