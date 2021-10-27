<template>
  <div>

    <div>

      <recursive-component
        :item="item"
        :index="index"
        v-for="(item, index) in Dir.contents"
        :key="index"/>
    </div>
  </div>
</template>
<script>
import RecursiveComponent from './RecursiveComponent';
export default {
  components: {
    RecursiveComponent
  },
    props: {
      Dir: [Object],
  },
  data() {
    return {

    }
  },
  methods: {

  }
}
</script>