<template>
  <span>
    <a @click="modalOpen = true" class="no-wrap">
      <Avatar :profile="profile" :address="address" size="16" class="mr-1" />
      {{ name }}
      <Badges :address="address" :space="space" />
    </a>
    <teleport to="#modal">
      <ModalUser
        :profile="profile"
        :open="modalOpen"
        @close="modalOpen = false"
        :space="space"
        :address="address"
      />
    </teleport>
  </span>
</template>

<script>
export default {
  props: ['address', 'space', 'profile'],
  data() {
    return {
      modalOpen: false
    };
  },
  computed: {
    name() {
      if (
        this.web3.account &&
        this.address.toLowerCase() === this.web3.account.toLowerCase()
      ) {
        return 'You';
      }
      if (this.profile?.name) {
        return this.profile.name;
      } else if (this.profile?.ens) {
        return this.profile.ens;
      }
      return this._shorten(this.address);
    }
  }
};
</script>
