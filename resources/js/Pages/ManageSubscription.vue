<template>
  <app-layout>
      <template #header>
          <h2 class="font-semibold text-xl text-gray-800 leading-tight">
              Manage Subscription
          </h2>
      </template>

      <div class="py-12">
          <div class="max-w-7xl mx-auto sm:px-6 lg:px-8">
              <div class="bg-white p-8 overflow-hidden shadow-xl sm:rounded-lg">
                  <h2 class="font-bold text-2xl">Hang on there! You need an active subscription before proceeding.</h2>
                  <p>
                    <jet-button class="mt-4" @click.native="checkout">Head to checkout page</jet-button>
                  </p>
              </div>
          </div>
      </div>
  </app-layout>
</template>

<script>
import JetButton from '../Jetstream/Button';
import AppLayout from '../Layouts/AppLayout';

export default {
  components: {
    JetButton,
    AppLayout
  },
  props: ['stripeKey', 'checkoutSessionId'],
  methods: {
    checkout() {
      window.Stripe(this.stripeKey).redirectToCheckout({
        sessionId: this.checkoutSessionId
      });
    }
  }
}
</script>