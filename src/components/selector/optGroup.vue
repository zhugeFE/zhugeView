<script type="text/jsx">
  import emitter from '../../mixins/emitter'
  import ZgGroupHeader from './groupHeader.vue'
  export default {
    components: {ZgGroupHeader},
    name: 'ZgOptGroup',
    mixins: [emitter],
    props: {
      groupData: {
        type: Object
      },
      store: {
        type: Array
      },
      checkedMap: {
        type: Object
      },
      showMap: {
        type: Object
      },
      disableOptions: {
        type: Array
      },
      keyField: {
        type: String,
        required: true
      },
      labelField: {
        type: String,
        required: true
      },
      /**
       * @description 图标
       */
      iconField: {
        type: String,
        default: ''
      },
      /**
       * @description 别名字段，设置别名后，优先展示别名
       */
      aliasField: {
        type: String
      },
      multiple: {
        type: Boolean,
        default: false
      },
      hideHead: {
        type: Boolean,
        default: false
      },
      /**
       * @description 主题，目前支持的主题有：normal、noborder、tag
       */
      theme: {
        type: String,
        default: 'normal',
        validator (value) {
          const themes = ['normal', 'noborder', 'tag']
          return themes.indexOf(value) > -1
        }
      }
    },
    data () {
      return {
        show: true
      }
    },
    methods: {
      onClickOption (checked, data) {
        this.$emit('click', checked, data)
      }
    },
    render (h) {
      return (
        <ul class="zg-opt-group" v-show={this.show}>
          <zg-group-header groupData={this.groupData}
                           labelField={this.labelField}
                           show={!this.hideHead}
                           scopedSlots={{default: this.$scopedSlots.header}}></zg-group-header>
          {this.store.map(option => {
            if (this.showMap[option[this.keyField]]) {
              return (
                <zg-option key={option[this.keyField]}
                           checked={this.checkedMap[option[this.keyField]]}
                           disable={this.disableOptions.indexOf(option[this.keyField]) > -1}
                           data={option}
                           labelField={this.labelField}
                           aliasField={this.aliasField}
                           iconField={this.iconField}
                           multiple={this.multiple}
                           theme={this.theme}
                           onClick={this.onClickOption}
                           scopedSlots={{default: this.$scopedSlots.default}}
                ></zg-option>
              )
            }
          })}
        </ul>
      )
    }
  }
</script>

<style lang="sass">
@import "styles/optGroup"
</style>
