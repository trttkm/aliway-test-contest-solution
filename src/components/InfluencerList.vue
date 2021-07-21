<template>
  <table>
    <thead>
    <tr>
      <td>Выбрано: {{ influencers.length }}</td>
      <InfluencerListSortButton
        title="Подписчиков"
        :handler=sortByFollowers
        :sort-direction=sortByFollowersDESC
      />
      <InfluencerListSortButton
        title="Рейтинг увлеченности"
        :handler=sortByEr
        :sort-direction=sortByErDESC
      />
    </tr>
    </thead>
    <tbody v-if="influencers.length > 0">
    <InfluencerItem
      v-for="influencer in influencers"
      :key="influencer.id"
      :influencer=influencer
    />
    </tbody>
    <tbody v-else>
    <tr>
      <td style="padding: 20px">Ничего не найдено</td>
    </tr>
    </tbody>
  </table>
</template>

<script>
import InfluencerItem from '@/components/InfluencerItem.vue';
import InfluencerListSortButton from '@/components/InfluencerListSortButton.vue';
import FieldService from '@/services/FieldService';

const fieldService = new FieldService();

export default {
  name: 'InfluencerList',
  components: {
    InfluencerListSortButton,
    InfluencerItem,
  },
  data() {
    return {
      influencers: [],
      sortByFollowersDESC: null,
      sortByErDESC: null,
    };
  },
  mounted() {
    /* не уверен что это правильно и что так можно делать,
       но не разобрался как по-другому получить массив с данными из сервиса */
    (async () => {
      this.influencers = await fieldService.getInfluencers();
    })();
  },
  methods: {
    sortByFollowers() {
      this.sortByErDESC = null;
      if (this.sortByFollowersDESC) {
        this.influencers.sort((a, b) => a.followers - b.followers);
        this.sortByFollowersDESC = false;
      } else {
        this.influencers.sort((a, b) => b.followers - a.followers);
        this.sortByFollowersDESC = true;
      }
    },
    sortByEr() {
      this.sortByFollowersDESC = null;
      if (this.sortByErDESC) {
        this.influencers.sort((a, b) => a.er - b.er);
        this.sortByErDESC = false;
      } else {
        this.influencers.sort((a, b) => b.er - a.er);
        this.sortByErDESC = true;
      }
    },
  },
};
</script>

<style lang="scss" scoped>
table {
  background-color: #fafafa;
  border-collapse: collapse;
  width: 700px;
}

thead td {
  font-weight: bold;
}

tr {
  border-bottom: 2px solid #bababa;

  tbody &:last-child {
    border-bottom: none;
  }

  &:hover {
    background-color: #e9fffa;
  }
}

td {
  padding: 20px;
}
</style>
