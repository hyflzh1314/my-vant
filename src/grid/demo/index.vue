<template>
  <demo-section>
    <demo-block :title="t('basicUsage')">
      <van-grid>
        <van-grid-item
          v-for="i in 4"
          :key="i"
          icon="photo-o"
          :text="t('text')"
        />
      </van-grid>
    </demo-block>

    <demo-block :title="t('columnNum')">
      <van-grid :column-num="3">
        <van-grid-item
          v-for="i in 6"
          :key="i"
          icon="photo-o"
          :text="t('text')"
        />
      </van-grid>
    </demo-block>

    <demo-block :title="t('customContent')">
      <van-grid :border="false" :column-num="3">
        <van-grid-item>
          <van-image
            fit="contain"
            src="https://img01.yzcdn.cn/vant/apple-1.jpg"
          />
        </van-grid-item>
        <van-grid-item>
          <van-image
            fit="contain"
            src="https://img01.yzcdn.cn/vant/apple-2.jpg"
          />
        </van-grid-item>
        <van-grid-item>
          <van-image
            fit="contain"
            src="https://img01.yzcdn.cn/vant/apple-3.jpg"
          />
        </van-grid-item>
      </van-grid>
    </demo-block>

    <demo-block :title="t('square')">
      <van-grid square>
        <van-grid-item
          v-for="i in 8"
          :key="i"
          icon="photo-o"
          :text="t('text')"
        />
      </van-grid>
    </demo-block>

    <demo-block :title="t('gutter')">
      <van-grid :gutter="10">
        <van-grid-item
          v-for="i in 8"
          :key="i"
          icon="photo-o"
          :text="t('text')"
        />
      </van-grid>
    </demo-block>

    <demo-block :title="t('horizontal')">
      <van-grid direction="horizontal" :column-num="3">
        <van-grid-item icon="photo-o" :text="t('text')" />
        <van-grid-item icon="photo-o" :text="t('text')" />
        <van-grid-item icon="photo-o" :text="t('text')" />
      </van-grid>
    </demo-block>

    <demo-block :title="t('route')">
      <van-grid clickable :column-num="2">
        <van-grid-item icon="home-o" :text="t('vueRoute')" to="/" />
        <van-grid-item
          icon="search"
          :text="t('urlRoute')"
          url="/vant/mobile.html"
        />
      </van-grid>
    </demo-block>

    <demo-block :title="t('showBadge')">
      <van-grid :column-num="2">
        <van-grid-item icon="home-o" :text="t('text')" dot />
        <van-grid-item icon="search" :text="t('text')" badge="99+" />
      </van-grid>
    </demo-block>
  </demo-section>
</template>

<script>
export default {
  i18n: {
    'zh-CN': {
      text: '??????',
      route: '????????????',
      gutter: '????????????',
      square: '???????????????',
      columnNum: '???????????????',
      customContent: '???????????????',
      urlRoute: 'URL ??????',
      vueRoute: '????????????',
      showBadge: '????????????',
      horizontal: '????????????',
    },
    'en-US': {
      text: 'Text',
      route: 'Route',
      gutter: 'Gutter',
      square: 'Square',
      columnNum: 'Column Num',
      customContent: 'Custom Content',
      urlRoute: 'URL',
      vueRoute: 'Vue Router',
      showBadge: 'Show Badge',
      horizontal: 'Horizontal',
    },
  },
};
</script>

<style lang="less">
@import '../../style/var';
</style>
