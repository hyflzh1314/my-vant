<template>
  <demo-section>
    <demo-block card :title="t('basicUsage')">
      <van-picker
        show-toolbar
        :title="t('title')"
        :columns="t('textColumns')"
        @change="onChange1"
      />
    </demo-block>

    <demo-block card :title="t('defaultIndex')">
      <van-picker
        show-toolbar
        :title="t('title')"
        :columns="t('textColumns')"
        :default-index="2"
        @change="onChange1"
      />
    </demo-block>

    <demo-block card :title="t('multipleColumns')">
      <van-picker
        show-toolbar
        :title="t('title')"
        :columns="t('dateColumns')"
        @cancel="onCancel"
        @confirm="onConfirm"
      />
    </demo-block>

    <demo-block card v-if="!isWeapp" :title="t('cascade')">
      <van-picker
        show-toolbar
        :title="t('title')"
        :columns="t('cascadeColumns')"
        @cancel="onCancel"
        @confirm="onConfirm"
      />
    </demo-block>

    <demo-block card :title="t('disableOption')">
      <van-picker
        show-toolbar
        :title="t('title')"
        :columns="t('disabledColumns')"
      />
    </demo-block>

    <demo-block card :title="t('setColumnValues')">
      <van-picker
        show-toolbar
        :title="t('title')"
        :columns="columns"
        @change="onChange2"
      />
    </demo-block>

    <demo-block card :title="t('loadingStatus')">
      <van-picker loading show-toolbar :title="t('title')" :columns="columns" />
    </demo-block>

    <demo-block card v-if="!isWeapp" :title="t('withPopup')">
      <van-field
        readonly
        clickable
        :label="t('city')"
        :value="fieldValue"
        :placeholder="t('chooseCity')"
        @click="onClickField"
      />
      <van-popup v-model="showPicker" round position="bottom">
        <van-picker
          show-toolbar
          :title="t('title')"
          :columns="t('textColumns')"
          @cancel="onCancel2"
          @confirm="onConfirm2"
        />
      </van-popup>
    </demo-block>
  </demo-section>
</template>

<script>
import { dateColumns, cascadeColumns } from './data';

export default {
  i18n: {
    'zh-CN': {
      city: '??????',
      cascade: '????????????',
      withPopup: '?????????????????????',
      chooseCity: '????????????',
      showToolbar: '???????????????',
      dateColumns: dateColumns['zh-CN'],
      defaultIndex: '???????????????',
      disableOption: '????????????',
      cascadeColumns: cascadeColumns['zh-CN'],
      multipleColumns: '????????????',
      setColumnValues: '??????????????????',
      textColumns: [
        '??????',
        '??????',
        '??????',
        '??????',
        '??????',
        '??????',
        '??????',
        '??????',
      ],
      disabledColumns: [
        { text: '??????', disabled: true },
        { text: '??????' },
        { text: '??????' },
      ],
      column3: {
        ??????: ['??????', '??????', '??????', '??????', '??????'],
        ??????: ['??????', '??????', '??????', '??????', '??????'],
      },
      toastContent: (value, index) => `????????????${value}, ???????????????${index}`,
    },
    'en-US': {
      city: 'City',
      cascade: 'Cascade',
      withPopup: 'With Popup',
      chooseCity: 'Choose City',
      showToolbar: 'Show Toolbar',
      dateColumns: dateColumns['en-US'],
      defaultIndex: 'Default Index',
      disableOption: 'Disable Option',
      cascadeColumns: cascadeColumns['en-US'],
      multipleColumns: 'Multiple Columns',
      setColumnValues: 'Set Column Values',
      textColumns: ['Delaware', 'Florida', 'Georqia', 'Indiana', 'Maine'],
      disabledColumns: [
        { text: 'Delaware', disabled: true },
        { text: 'Florida' },
        { text: 'Georqia' },
      ],
      column3: {
        Group1: ['Delaware', 'Florida', 'Georqia', 'Indiana', 'Maine'],
        Group2: ['Alabama', 'Kansas', 'Louisiana', 'Texas'],
      },
      toastContent: (value, index) => `Value: ${value}, Index???${index}`,
    },
  },

  data() {
    return {
      showPicker: false,
      fieldValue: '',
    };
  },

  computed: {
    columns() {
      const column = this.t('column3');
      return [
        {
          values: Object.keys(column),
          className: 'column1',
        },
        {
          values: column[Object.keys(column)[0]],
          className: 'column2',
          defaultIndex: 2,
        },
      ];
    },
  },

  methods: {
    onChange1(picker, value, index) {
      this.$toast(this.t('toastContent', value, index));
    },

    onChange2(picker, values) {
      picker.setColumnValues(1, this.t('column3')[values[0]]);
    },

    onConfirm(value, index) {
      this.$toast(this.t('toastContent', value, index));
    },

    onCancel() {
      this.$toast(this.t('cancel'));
    },

    onClickField() {
      this.showPicker = true;
    },

    onConfirm2(value) {
      this.showPicker = false;
      this.fieldValue = value;
    },

    onCancel2() {
      this.showPicker = false;
    },
  },
};
</script>
