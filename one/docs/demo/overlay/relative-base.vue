<template>
<article>
  <veui-button
    ref="toggle"
    @click="open = !open"
  >
    Toggle
  </veui-button>
  <veui-overlay
    target="toggle"
    position="top-start"
    :open.sync="open"
    overlay-class="relative-overlay"
  >
    <div v-outside:toggle="hide">
      Relatively Positioned
    </div>
  </veui-overlay>
</article>
</template>

<script>
import { Overlay, Button } from 'veui'
import outside from 'veui/directives/outside'

export default {
  components: {
    'veui-overlay': Overlay,
    'veui-button': Button
  },
  directives: { outside },
  data () {
    return {
      open: false
    }
  },
  methods: {
    hide () {
      this.open = false
    }
  }
}
</script>

<style lang="less" src="./relative.less" docs></style>
