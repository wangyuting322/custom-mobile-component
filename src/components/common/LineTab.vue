<script>
/**
 * 线性tab
 */
export default {
  name: 'LineTab',
  components: {},
  props: {
    /**
     * 含value和label属性的对象数组 - value为tab的值，label为显示的值
     */
    tabList: {
      type: Array,
      requred: true
    },
    value: {
      type: String
    }
  },
  model: {
    prop: 'value',
    event: 'change'
  },
  data () {
    return {
      offsetLeft: 0,
      clientWidth: 0,
      randomNum: (new Date()).getTime() + parseInt((Math.random()) * 1000)
    }
  },
  computed: {},
  methods: {
    handleTab (tab) {
      this.$emit('change', tab)
    }
  },
  watch: {
    value: {
      handler (newV) {
        if (newV) {
          this.$nextTick(() => {
            // 获取选中的tab元素
            const tabItem = document.querySelector(`.line-tab-item${this.randomNum}${newV}`)
            if (tabItem) {
              // 获取线
              const line = this.$refs[`line${this.randomNum}`]
              line.style.left = tabItem.offsetLeft + 'px'
              line.style.width = tabItem.clientWidth + 'px'
            }
          })
        }
      },
      immediate: true
    }
  },
  created () {},
  mounted () {},
  render (h) {
    return (
      <div class={'line-tab fs14'}>
        {this.tabList.map((item, index) => {
          const { value, label } = item
          return (
            <div
              class={`line-tab-item pt14 pb14 pointer ${
                this.value === value ? 'line-tab-active' : ''
              } line-tab-item${this.randomNum}${value}`}
              onClick={(e) => this.handleTab(value, e)}
            >
              {label}
            </div>
          )
        })}
        <div class="line-tab-line" ref={`line${this.randomNum}`}></div>
      </div>
    )
  }
}
</script>
<style lang="scss" scoped>
.line-tab {
  overflow: hidden;
  background-color: #fff;
  position: relative;
  display: flex;
  flex-direction: row;
  justify-content: space-around;
  &-item {
    display: flex;
    flex-direction: column;
    color: #363a44;
  }
  &-active {
    color: #428ffc;
  }
  &-line {
    position: absolute;
    bottom: 0;
    left: 0;
    width: 0px;
    height: 2px;
    background-color: #428ffc;
    transition: all 0.3s ease;
  }
}
</style>
