<template>
  <Card :class="subscriptionCardClasses">
    <template #header>
      <div class="subscription-card__header">{{ $t(data.name) }}</div>
    </template>
    <template #content>
      <p class="subscription-card__description">{{ $t(data.description) }}</p>
      <p class="subscription-card__pricing">{{ data.pricing }}</p>
      <SubscriptionCardButton :variation="data.type" class="w-full" />
    </template>
  </Card>
</template>
<script>
import Card from 'primevue/card'
import SubscriptionCardButton from '@components/atoms/buttons/SubscriptionCardButton.vue'

import Subscription from '@entities/Subscription'

export default {
  components: {
    Card,
    SubscriptionCardButton
  },
  props: {
    data: {
      required: true,
      type: Subscription
    }
  },
  computed: {
    subscriptionCardClasses() {
      return ['subscription-card', `subscription-card--${this.data.type}`]
    }
  }
}
</script>
<style lang="scss">
.subscription-card {
  max-width: 300px;

  &__header {
    padding: 1.25rem;
    font-size: 1.5rem;
    border-radius: 6px 6px 0 0;
  }

  &__description {
    margin-bottom: 1rem;
    min-height: 60px;
  }

  &__pricing {
    font-weight: 700;
    font-size: 1.25rem;
    margin-bottom: 1rem;
  }

  &--professional {
    .subscription-card__header {
      background-color: var(--green-400);
      color: var(--gray-50);
    }
  }

  &--student {
    .subscription-card__header {
      background-color: var(--blue-400);
      color: var(--gray-50);
    }
  }
}
</style>
