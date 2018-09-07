<template>
<ul class="container">
  <li class="flex"><img src="../assets/logo.png"></li>
  <li class="flex"><img src="../assets/logo.png"></li>
  <li class="flex"><img src="../assets/logo.png"></li>
  <li class="flex"><img src="../assets/logo.png"></li>
  <button @click="fff()">click</button>
</ul>
</template>

<script>
export default {
  methods: {
    asyncFn1 () {
      console.log('asyncFn1')
      return new Promise((resolve, reject) => {
        setTimeout(() => {
          resolve()
        }, 1000)
      })
    },
    asyncFn2 () {
      console.log('asyncFn2')
      return new Promise((resolve, reject) => {
        setTimeout(() => {
          resolve()
        }, 1000)
      })
    },
    nomorlFn () {
      console.log('nomorlFn')
    },
    fff () {
      this.asyncFn1().then(this.asyncFn2).then(this.nomorlFn)
    }
  }
}
</script>

<style>
.container {
  /* width: 800px;
  height: 200px; */
  display: flex;
  flex-wrap: wrap;
  padding-inline-start: 0px;
}
.flex {
  list-style-type: none;
  background: red;
  /* margin: 20px; */
  /* flex: 1; */
  width: 50%;
}
</style>
