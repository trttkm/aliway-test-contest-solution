<template>
  <td class="sort-btn" @click="handler">
    {{ title }}
    <font-awesome-icon v-if="sortDirection === true" icon="chevron-down" />
    <font-awesome-icon v-else-if="sortDirection === false" icon="chevron-up" />
  </td>
</template>

<script>
import { library } from '@fortawesome/fontawesome-svg-core';
import { faChevronUp, faChevronDown } from '@fortawesome/free-solid-svg-icons';

library.add(faChevronUp, faChevronDown);

export default {
  name: 'InfluencerListSortButton',
  props: {
    title: String,
    handler: Function,
    sortDirection: Boolean || null,
  },
};
</script>

<style lang="scss" scoped>
.sort-btn {
  text-align: right;
  cursor: pointer;

  &:hover {
    background-color: #97dcbd;
  }
}
</style>
