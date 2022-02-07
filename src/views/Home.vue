<script>
export default {
  name: 'Home',
  components: {

  },
  props: {

  },
  data () {
    return {
      tabList: [
        {
          value: 'tab1',
          label: 'tab1'
        }, {
          value: 'tab2',
          label: 'tab2'
        }
      ],
      activeCardTab: 'tab1',
      activeLineTab: 'tab2'
    }
  },
  computed: {

  },
  methods: {

  },
  watch: {

  },
  created () {

  },
  mounted () {

  },
  beforeDestroy () {

  },
  render (h) {
    return (
      <div>
        <div class="home fade">
          <CardTab tabList = {this.tabList} v-model={this.activeCardTab}></CardTab>
          <LineTab tabList = {this.tabList} v-model={this.activeLineTab}></LineTab>
        </div>
      </div>
    )
  }
}
</script>
<style lang="scss" scoped>
.home{
  height:100%;
}
</style>
