<template>
  <div class="filter__max sf-review_">
    <div class="sf-review__rating">
      <SwRating
        :score="Number.parseInt(max)"
        :max="5"
        :hover-effect="true"
        @click="emitClick"
      />
    </div>
  </div>
</template>
<script>
import { computed, ref } from "@vue/composition-api"
import { SfRating, SfIcon } from "@storefront-ui/vue"
import SwRating from "@shopware-pwa/default-theme/components/atoms/SwRating"

export default {
  components: {
    SfRating,
    SfIcon,
    SwRating,
  },
  props: {
    filter: {
      type: Object,
      default: () => ({}),
    },
    max: {
      type: Number | Boolean,
      default: () => ({}),
    },
  },
  methods: {
    emitClick(item) {
      this.$emit("toggle-select", {
        type: "max",
        max: item,
        field: this.filter.name,
      })
    },
  },
}
</script>
<style lang="scss" scoped>
.filter {
  &__range {
    display: flex;
    flex: 1 1;
  }
}

.rating {
  &__positive {
    --icon-color: var(--c-primary);
  }
  &__negative {
    --icon-color: var(--c-gray-variant);
  }
}
</style>
