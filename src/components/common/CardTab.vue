<script>
/**
 * 卡片tab
 */
export default {
  name: 'CardTab',
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

    }
  },
  computed: {},
  methods: {
    handleTab (tab) {
      this.$emit('change', tab)
    }
  },
  watch: {
  },
  created () { },
  mounted () { },
  render (h) {
    return (
      <div class="card-tab width100 border-box flex-row">
        {this.tabList.map((item) => {
          const { value, label } = item
          return (
            <div
              class={`ellipsis  border-box flex-grow fs16 pt6 pb6 pointer flex-ai-center card-tab-item flex-row flex-jc-center ${this.value === value ? 'card-tab-active' : ''
                }`}
              onClick={() => this.handleTab(value)}
            >
              {label}
            </div>
          )
        })}
      </div>
    )
  }
}
</script>
<style lang="scss" scoped>
.card-tab {
  border-radius: 0.4rem;
  border: 1px solid #428ffc;
  overflow: hidden;
  & > div:not(:last-child) {
    border-right: 1px solid #428ffc;
  }
  &-item {
    background-color: #fff;
    color: $primary-color;
  }
  &-active {
    background-color: $primary-color;
    color: white;
  }
}
</style>
