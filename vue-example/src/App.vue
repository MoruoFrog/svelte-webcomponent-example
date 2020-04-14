<template>
  <div>
    <p>Web component compiled by Svelte，used in Vue</p>

    <svelte-component
      ref="test"
      id="test"
      :name="name"
      :objprop.prop="objProp"
      v-on:eventTest="handleEvent"
      >
    </svelte-component>

    <hr>

    <div>
      <label>输入name <input type="text" v-model="name"></label>
    </div>

    <div>
      <button @click="setObjProp">click to toggle object prop</button>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      name: 'world',
      objProp: {
        name: 'in Vue',
      }
    }
  },

  methods: {
    setObjProp() {
      this.objProp =  this.objProp.name === 'in Vue' 
        ? { name: 'new object prop' }
        : { name: 'in Vue' }
    },
    handleEvent(e) {
      console.log(e)
      alert(e.detail.text)
    }
  },

  mounted() {
    // 也可以这样监听
    // this.$refs.test.addEventListener('eventTest', this.handleEvent);
    // this.$refs.test.$on('eventTest', this.handleEvent);
  }
}
</script>

<style scoped>
div {
  text-align: center;
} 
p {
  font-size: 30px;
  margin-top: 100px;
}

button {
  margin-top: 20px;
  padding: 5px 20px;
}
</style>