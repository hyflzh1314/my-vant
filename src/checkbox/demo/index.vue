<template>
  <demo-section>
    <demo-block :title="t('basicUsage')">
      <van-checkbox v-model="checkbox1">{{ t('checkbox') }}</van-checkbox>
    </demo-block>

    <demo-block :title="t('disabled')">
      <van-checkbox :value="false" disabled>
        {{ t('checkbox') }}
      </van-checkbox>
      <van-checkbox :value="true" disabled>
        {{ t('checkbox') }}
      </van-checkbox>
    </demo-block>

    <demo-block :title="t('customShape')">
      <van-checkbox v-model="checkboxShape" shape="square">
        {{ t('customColor') }}
      </van-checkbox>
    </demo-block>

    <demo-block :title="t('customColor')">
      <van-checkbox v-model="checkbox2" checked-color="#ee0a24">
        {{ t('customColor') }}
      </van-checkbox>
    </demo-block>

    <demo-block :title="t('customIconSize')">
      <van-checkbox v-model="checboxIcon" icon-size="24px">
        {{ t('customIconSize') }}
      </van-checkbox>
    </demo-block>

    <demo-block :title="t('customIcon')">
      <van-checkbox v-model="checkbox3">
        {{ t('customIcon') }}
        <template #icon="{ checked }">
          <img :src="checked ? activeIcon : inactiveIcon" />
        </template>
      </van-checkbox>
    </demo-block>

    <demo-block :title="t('disableLabel')">
      <van-checkbox v-model="checkboxLabel" label-disabled>
        {{ t('checkbox') }}
      </van-checkbox>
    </demo-block>

    <demo-block :title="t('title3')">
      <van-checkbox-group v-model="result">
        <van-checkbox name="a">{{ t('checkbox') }} a</van-checkbox>
        <van-checkbox name="b">{{ t('checkbox') }} b</van-checkbox>
      </van-checkbox-group>
    </demo-block>

    <demo-block v-if="!isWeapp" :title="t('horizontal')">
      <van-checkbox-group v-model="horizontalResult" direction="horizontal">
        <van-checkbox name="a">{{ t('checkbox') }} a</van-checkbox>
        <van-checkbox name="b">{{ t('checkbox') }} b</van-checkbox>
      </van-checkbox-group>
    </demo-block>

    <demo-block :title="t('title4')">
      <van-checkbox-group v-model="result2" :max="2">
        <van-checkbox name="a">{{ t('checkbox') }} a</van-checkbox>
        <van-checkbox name="b">{{ t('checkbox') }} b</van-checkbox>
        <van-checkbox name="c">{{ t('checkbox') }} c</van-checkbox>
      </van-checkbox-group>
    </demo-block>

    <demo-block v-if="!isWeapp" :title="t('toggleAll')">
      <van-checkbox-group v-model="checkAllResult" ref="group">
        <van-checkbox name="a">{{ t('checkbox') }} a</van-checkbox>
        <van-checkbox name="b">{{ t('checkbox') }} b</van-checkbox>
        <van-checkbox name="c">{{ t('checkbox') }} c</van-checkbox>
      </van-checkbox-group>

      <div class="demo-checkbox-buttons">
        <van-button type="primary" @click="checkAll">
          {{ t('checkAll') }}
        </van-button>
        <van-button type="info" @click="toggleAll">
          {{ t('inverse') }}
        </van-button>
      </div>
    </demo-block>

    <demo-block :title="t('title5')">
      <van-checkbox-group v-model="result3">
        <van-cell-group>
          <van-cell
            v-for="(item, index) in list"
            clickable
            :key="index"
            :title="`${t('checkbox')} ${item}`"
            @click="toggle(index)"
          >
            <template #right-icon>
              <van-checkbox ref="checkboxes" :name="item" />
            </template>
          </van-cell>
        </van-cell-group>
      </van-checkbox-group>
    </demo-block>
  </demo-section>
</template>

<script>
export default {
  i18n: {
    'zh-CN': {
      checkbox: '?????????',
      customIcon: '???????????????',
      customIconSize: '???????????????',
      customColor: '???????????????',
      customShape: '???????????????',
      title3: '????????????',
      title4: '?????????????????????',
      title5: '???????????????????????????',
      toggleAll: '???????????????',
      checkAll: '??????',
      inverse: '??????',
      horizontal: '????????????',
      disableLabel: '??????????????????',
    },
    'en-US': {
      checkbox: 'Checkbox',
      customIcon: 'Custom Icon',
      customIconSize: 'Custom Icon Size',
      customColor: 'Custom Color',
      customShape: 'Custom Shape',
      title3: 'Checkbox Group',
      title4: 'Maximum amount of checked options',
      title5: 'Inside a Cell',
      toggleAll: 'Toggle All',
      checkAll: 'Check All',
      inverse: 'Inverse',
      horizontal: 'Horizontal',
      disableLabel: 'Disable label click',
    },
  },

  data() {
    return {
      checkbox1: true,
      checkbox2: true,
      checkbox3: true,
      checkboxShape: true,
      checkboxLabel: true,
      checboxIcon: true,
      list: ['a', 'b'],
      result: ['a', 'b'],
      result2: [],
      result3: [],
      checkAllResult: [],
      horizontalResult: [],
      activeIcon: 'https://img01.yzcdn.cn/vant/user-active.png',
      inactiveIcon: 'https://img01.yzcdn.cn/vant/user-inactive.png',
    };
  },

  methods: {
    toggle(index) {
      this.$refs.checkboxes[index].toggle();
    },

    checkAll() {
      this.$refs.group.toggleAll(true);
    },

    toggleAll() {
      this.$refs.group.toggleAll();
    },
  },
};
</script>

<style lang="less">
@import '../../style/var';

.demo-checkbox {
  background: @white;

  .van-checkbox {
    margin: 0 0 8px 20px;
  }

  .van-cell {
    .van-checkbox {
      margin: 0;
    }
  }

  img {
    height: 20px;
  }

  &-buttons {
    margin-top: @padding-md;

    .van-button {
      margin-left: @padding-md;
    }
  }

  .van-doc-demo-block__title {
    margin-top: -8px;
  }
}
</style>
