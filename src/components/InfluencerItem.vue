<template>
  <tr>
    <td class="influencer-info">
      <img class="influencer-info__avatar" :src="influencer.avatarUrl" :alt="influencer.name">
      <div class="influencer-info__details">
        <div class="influencer-info__name">@{{ influencer.name }}</div>
        <a class="influencer-info__link" :href="influencer.profileUrl" target="_blank">Instagram</a>
      </div>
    </td>
    <td class="influencer-numbers">
      {{ new Intl.NumberFormat('ru-RU').format(influencer.followers) }}
    </td>
    <td class="influencer-numbers">{{ influencer.er }}%</td>
  </tr>
</template>

<script>
import Influencer from '@/services/models/Influencer';

export default {
  name: 'InfluencerItem',
  props: {
    influencer: Influencer,
  },
};
</script>

<style lang="scss" scoped>
.influencer {
  &-info {
    display: flex;
    align-items: center;
    padding: 20px;

    &__avatar {
      width: 70px;
      height: 70px;
      border-radius: 50%;
    }

    &__details {
      margin-left: 20px;
    }

    &__name {
      font-weight: bold;
    }

    &__link {
      text-decoration: none;
      color: darkgrey
    }
  }

  &-numbers {
    text-align: right;
    padding: 20px;
  }
}
</style>
