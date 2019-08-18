<template>
  <div class="hello">
    <p>msg: {{ msg }}</p>
    <p>testObjName: {{ testObj.name }}</p>
    <p>testObjNameUpper: {{ capPropsName }}</p>
    <p>testObjTitle: {{ testObj.title }}</p>
    <button v-on:click="emitFunc">EmitFunc</button>
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  data() {
    return {
      childMsg: 'Msg From Child',
    }
  },
  methods: {
    emitFunc() {
      console.log(`triggerFromChild${this.childMsg}`)

      // 首個變數為要觸發的事件名稱 後為要傳遞的變數
      this.$emit('testBBB', this.childMsg)
    },
  },
  computed: {
    // capPropsName: this.props.testObj.name.toUpperCase(),
    capPropsName() {
      return this.msg.toUpperCase()
    },
  },
  props: {
    msg: {
      type: String,
      // 注意不可使用 data/computed,props於beforeCreated建立
      // default: () => { 'test' },
      default: 'test',
      // 必須符合陣列中的值 才會通過
      // validator: value => (['test123'].indexOf(value) !== -1),
    },
    testObj: {
      type: Object,
      required: true,
    },
  },
}
</script>

<style scoped lang="scss">
  .test {
    color: $primary;
  }
  h3 {
    margin: 40px 0 0;
  }
  ul {
    list-style-type: none;
    padding: 0;
  }
  li {
    display: inline-block;
    margin: 0 10px;
  }
  a {
    color: #42b983;
  }
</style>
