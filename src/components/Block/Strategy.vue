<template>
  <Block>
    <div class="d-flex flex-items-baseline">
      <h3>
        {{ strategy.key }}
      </h3>
      <div class="ml-1">v{{ strategy.version }}</div>
    </div>
    <div class="text-gray">
      <Icon name="github" class="mr-1" />
      {{ strategy.author }}
    </div>
    <div>In {{ _n(strategy.spaces.length) }} space(s)</div>
  </Block>
</template>

<script>
export default {
  props: ['strategy']
};
</script>
