<template>
  <div>
    <div>
      <div>
        <ul v-if="item.contents && item.contents.length > 0">
          <h3 class="dir-name" @click="changeVisability">folder name: {{ item.name }}</h3>
          <recursive-component
            v-for="(child, subIndex) in item.contents"
            :item="child"
            :key="subIndex"
            v-show="isVisible"

            />
        </ul>
      </div>
    </div>
    <li
        v-if="item.type === 'file'"
        class="file-name"
        @click="selected"
        >
        {{item.name}}
        </li>
    <li v-if="item.type === 'link'"
        class="link-name"
        @click="selected"
        >
        {{item.name}}
        </li>

  </div>
</template>
<script>
export default {
  name: "RecursiveComponent",
  props: {
    item: {
      type: [Object, String],
      required: true
    },

  },
    data: () => ({
      isVisible: false,
    }),
  methods: {
    changeVisability() {
      this.isVisible = !this.isVisible;
    },
    selected(e) {
      e.target.classList.toggle('selected');
    }
  }
}
</script>
<style scoped>

.dir-name{
  color: tomato;
}
.file-name {
  color: brown;
}
.link-name {
  color: blue;
}
.selected {
  color: green;
}

</style>