<template>
  <demo-section>
    <demo-block :title="t('type')">
      <div class="demo-button-row">
        <van-button type="primary">{{ t('primary') }}</van-button>
        <van-button type="info">{{ t('info') }}</van-button>
        <van-button type="default">{{ t('default') }}</van-button>
      </div>
      <van-button type="danger">{{ t('danger') }}</van-button>
      <van-button type="warning">{{ t('warning') }}</van-button>
    </demo-block>

    <demo-block :title="t('plain')">
      <van-button plain type="primary" :text="t('plain')" />
      <van-button plain type="info" :text="t('plain')" />
    </demo-block>

    <demo-block :title="t('hairline')">
      <van-button plain hairline type="primary" :text="t('hairlineButton')" />
      <van-button plain hairline type="info" :text="t('hairlineButton')" />
    </demo-block>

    <demo-block :title="t('disabled')">
      <van-button disabled type="primary" :text="t('disabled')" />
      <van-button disabled type="info" :text="t('disabled')" />
    </demo-block>

    <demo-block :title="t('loadingStatus')">
      <van-button loading type="primary" />
      <van-button loading type="primary" loading-type="spinner" />
      <van-button loading :loading-text="t('loadingText')" type="info" />
    </demo-block>

    <demo-block :title="t('shape')">
      <van-button type="primary" square :text="t('square')" />
      <van-button type="info" round :text="t('round')" />
    </demo-block>

    <demo-block :title="t('icon')">
      <van-button type="primary" icon="plus" />
      <van-button type="primary" icon="plus" :text="t('button')" />
      <van-button
        plain
        type="info"
        icon="https://img01.yzcdn.cn/vant/user-active.png"
        :text="t('button')"
      />
    </demo-block>

    <demo-block :title="t('size')">
      <van-button type="primary" size="large">{{ t('large') }}</van-button>
      <van-button type="primary" size="normal">{{ t('normal') }}</van-button>
      <van-button type="primary" size="small">{{ t('small') }}</van-button>
      <van-button type="primary" size="mini">{{ t('mini') }}</van-button>
    </demo-block>

    <demo-block :title="t('blockElement')">
      <van-button type="primary" block>{{ t('blockElement') }}</van-button>
    </demo-block>

    <demo-block v-if="!isWeapp" :title="t('router')">
      <van-button
        :text="t('urlRoute')"
        type="primary"
        url="/vant/mobile.html"
      />
      <van-button :text="t('vueRoute')" type="primary" to="index" />
    </demo-block>

    <demo-block :title="t('customColor')">
      <van-button color="#7232dd" :text="t('pure')" />
      <van-button plain color="#7232dd" :text="t('pure')" />
      <van-button
        color="linear-gradient(to right, #ff6034, #ee0a24)"
        :text="t('gradient')"
      />
    </demo-block>
  </demo-section>
</template>

<script>
export default {
  i18n: {
    'zh-CN': {
      type: '????????????',
      size: '????????????',
      icon: '????????????',
      loading: '????????????',
      shape: '????????????',
      default: '????????????',
      primary: '????????????',
      info: '????????????',
      danger: '????????????',
      warning: '????????????',
      large: '????????????',
      normal: '????????????',
      small: '????????????',
      mini: '????????????',
      plain: '????????????',
      square: '????????????',
      round: '????????????',
      hairline: '?????????',
      hairlineButton: '???????????????',
      loadingText: '?????????...',
      router: '????????????',
      urlRoute: 'URL ??????',
      vueRoute: '????????????',
      customColor: '???????????????',
      pure: '????????????',
      gradient: '???????????????',
      blockElement: '????????????',
    },
    'en-US': {
      type: 'Type',
      size: 'Size',
      icon: 'Icon',
      loading: 'Loading',
      shape: 'Shape',
      default: 'Default',
      primary: 'Primary',
      info: 'Info',
      danger: 'Danger',
      warning: 'Warning',
      large: 'Large',
      normal: 'Normal',
      small: 'Small',
      mini: 'Mini',
      plain: 'Plain',
      square: 'Square',
      round: 'Round',
      hairline: 'Hairline',
      hairlineButton: 'Hairline',
      loadingText: 'Loading...',
      router: 'Router',
      urlRoute: 'URL',
      vueRoute: 'Vue Router',
      customColor: 'Custom Color',
      pure: 'Pure',
      gradient: 'Gradient',
      blockElement: 'Block Element',
    },
  },
};
</script>

<style lang="less">
@import '../../style/var';

.demo-button {
  .van-button {
    &--large {
      margin-bottom: @padding-md;
    }

    &--small,
    &--normal:not(:last-child) {
      margin-right: @padding-md;
    }
  }

  .van-doc-demo-block {
    padding: 0 @padding-md;
  }

  .van-doc-demo-block__title {
    padding-left: 0;
  }

  &-row {
    margin-bottom: @padding-sm;
  }
}
</style>
