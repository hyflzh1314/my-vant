<template>
  <demo-section>
    <van-cell is-link @touchstart.native.stop="keyboard = 'default'">
      {{ t('button1') }}
    </van-cell>
    <van-cell is-link @touchstart.native.stop="keyboard = 'custom'">
      {{ t('button2') }}
    </van-cell>
    <van-cell is-link @touchstart.native.stop="keyboard = 'extraKey'">
      {{ t('button3') }}
    </van-cell>
    <van-cell is-link @touchstart.native.stop="keyboard = 'title'">
      {{ t('button4') }}
    </van-cell>
    <van-cell is-link @touchstart.native.stop="keyboard = 'multiExtraKey'">
      {{ t('button5') }}
    </van-cell>
    <van-cell is-link @touchstart.native.stop="keyboard = 'randomKeyOrder'">
      {{ t('button6') }}
    </van-cell>

    <van-field
      readonly
      clickable
      :value="value"
      :label="t('bindValue')"
      :placeholder="t('clickToInput')"
      @touchstart.native.stop="keyboard = 'bindValue'"
    />

    <van-number-keyboard
      :show="keyboard === 'default'"
      @blur="keyboard = ''"
      @input="onInput"
      @delete="onDelete"
    />

    <van-number-keyboard
      :show="keyboard === 'custom'"
      :close-button-text="t('close')"
      theme="custom"
      extra-key="."
      @blur="keyboard = ''"
      @input="onInput"
      @delete="onDelete"
    />

    <van-number-keyboard
      :show="keyboard === 'extraKey'"
      :close-button-text="t('close')"
      extra-key="X"
      @blur="keyboard = ''"
      @input="onInput"
      @delete="onDelete"
    />

    <van-number-keyboard
      :show="keyboard === 'title'"
      :close-button-text="t('close')"
      :title="t('title')"
      extra-key="."
      @blur="keyboard = ''"
      @input="onInput"
      @delete="onDelete"
    />

    <van-number-keyboard
      :show="keyboard === 'multiExtraKey'"
      :close-button-text="t('close')"
      theme="custom"
      :extra-key="['00', '.']"
      @blur="keyboard = ''"
      @input="onInput"
      @delete="onDelete"
    />

    <van-number-keyboard
      v-if="!isTest"
      :show="keyboard === 'randomKeyOrder'"
      random-key-order
      @blur="keyboard = ''"
      @input="onInput"
      @delete="onDelete"
    />

    <van-number-keyboard
      v-model="value"
      :show="keyboard === 'bindValue'"
      maxlength="6"
      @blur="keyboard = ''"
    />
  </demo-section>
</template>

<script>
export default {
  i18n: {
    'zh-CN': {
      close: '??????',
      input: '??????',
      title: '????????????',
      button1: '??????????????????',
      button2: '???????????????????????????',
      button3: '????????????????????????',
      button4: '????????????????????????',
      button5: '?????????????????????????????????',
      button6: '?????????????????????????????????',
      extraKey: '?????????????????????',
      bindValue: '????????????',
      clickToInput: '????????????',
      multiExtraKey: '??????????????????',
      randomKeyOrder: '??????????????????',
    },
    'en-US': {
      close: 'Close',
      input: 'Input',
      title: 'Keyboard Title',
      button1: 'Show Default Keyboard',
      button2: 'Show Keyboard With Sidebar',
      button3: 'Show IdNumber Keyboard',
      button4: 'Show Keyboard With Title',
      button5: 'Show Keyboard With Multiple ExtraKey',
      button6: 'Show Keyboard With Random Key Order',
      bindValue: 'Bind Value',
      clickToInput: 'Click To Input',
      extraKey: 'IdNumber Keyboard',
      multiExtraKey: 'Multiple ExtraKey',
      randomKeyOrder: 'Random Key Order',
    },
  },

  data() {
    return {
      value: '',
      keyboard: 'default',
      isTest: process.env.NODE_ENV === 'test',
    };
  },

  methods: {
    onInput(value) {
      this.$toast(`${this.t('input')}: ${value}`);
    },

    onDelete() {
      this.$toast(this.t('delete'));
    },
  },
};
</script>

<style lang="less">
@import '../../style/var';

.demo-number-keyboard {
  padding-bottom: 300px;

  .van-button {
    margin-left: @padding-md;
  }
}
</style>
