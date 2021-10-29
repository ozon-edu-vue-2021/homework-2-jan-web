<template>
  <div>

    <div>

      <recursive-component
        :item="item"
        :index="index"
        v-for="(item, index) in [...Dir]"
        :key="index"
        :isFileSelected="isFileSelected"
        @file="fileSelected"
        />
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
    isFileSelected: true
    }
  },
  methods: {
     fileSelected() {
			this.isFileSelected = false;
    },
  }

}
</script>
