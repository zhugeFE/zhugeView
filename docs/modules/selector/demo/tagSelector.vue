<template>
  <div>
    <demo-panel subtitle="tag模式">
      <zg-selector :store="[]" labelField="label" keyField="key"></zg-selector>
      <zg-selector keyField="id"
                   :store="store"
                   placeholder="单选"
                   labelField="label"
                   filterOption
                   icon-field="icon"
                   theme="tag"
                   multiple
                   :search="onSearch"
                   :maxWidth="450"
                   v-model="result">
      </zg-selector>
    </demo-panel>
  </div>
</template>

<script>
  import {util} from '../../../../src/utils'
  export default {
    name: 'tagSelector',
    data () {
      return {
        store: (() => {
          let store = []
          for (let i = 0; i < 20; i++) {
            store.push({
              id: i,
              label: 'option_' + i,
              icon: 'zgicon-edit'
            })
          }
          return store
        })(),
        result: []
      }
    },
    methods: {
      onSearch (val) {
        return new Promise((resolve) => {
          let store = []
          for (let i = 0; i < 20; i++) {
            store.push({
              id: Math.random().toString().split('.')[1],
              label: 'option_' + util.random(0, 1000),
              icon: 'zgicon-edit'
            })
          }
          this.store = store
          resolve()
        })
      }
    }
  }
</script>

<style lang="sass">

</style>
