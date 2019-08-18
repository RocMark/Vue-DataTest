<template>
  <div class="home">

    <div class="homeBorder">
      <p>HomePage</p>
      <p>msg: {{ msg }}</p>
      <p>listenData: {{ listenData }}</p>
      <p>testObj: {{ testObj }}</p>
    </div>

    <!-- 綁定 emit 事件 & 傳遞 Props 物件 不可使用縮寫!!!! -->
    <HelloWorld v-on:testBBB="getChildMsg" class="homeBorder" msg v-bind:testObj=testObj />

  </div>
</template>

<script>
// @ is an alias to /src
import HelloWorld from '@/components/HelloWorld.vue'

export default {
  name: 'home',
  data() {
    return {
      msg: 'msgData',
      childMsg: 'Default',
      testObj: {
        name: 123,
        title: 'TW NO.1',
      },
    }
  },
  computed: {
    listenData() {
      return this.childMsg.toUpperCase()
    },
  },
  methods: {
    getChildMsg(data) {
      console.log(`ParentGet:${data}`)
      this.childMsg = data
      console.log(`listenData${this.listenData}`)
    },
  },
  components: {
    HelloWorld,
  },
  created() {
    // this.$store
    //   .dispatch('getUsers')
    //   .then((result) => {
    //     this.users = result.data
    //     console.table(result.data)
    //   })
    //   .catch((err) => {
    //     console.error(err)
    //   })
  },
}
</script>

<style lang="scss" scoped>
.homeBorder {
  border: .5px solid #000;
  margin: 2vh 5vw;
  padding: 2rem;
}
</style>
