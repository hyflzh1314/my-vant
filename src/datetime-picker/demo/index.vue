<template>
  <demo-section>
    <demo-block card :title="t('dateType')">
      <van-datetime-picker
        v-model="value.date"
        type="date"
        :title="t('dateType')"
        :min-date="minDate"
        :max-date="maxDate"
      />
    </demo-block>

    <demo-block card :title="t('yearMonthType')">
      <van-datetime-picker
        v-model="value.yearMonth"
        type="year-month"
        :title="t('yearMonthType')"
        :min-date="minDate"
        :max-date="maxDate"
        :formatter="formatter"
      />
    </demo-block>

    <demo-block v-if="!isWeapp" card :title="t('monthDayType')">
      <van-datetime-picker
        v-model="value.monthDayType"
        type="month-day"
        :title="t('monthDayType')"
        :min-date="minDate"
        :max-date="maxDate"
        :formatter="formatter"
      />
    </demo-block>

    <demo-block card :title="t('timeType')">
      <van-datetime-picker
        v-model="value.time"
        type="time"
        :title="t('timeType')"
        :min-hour="10"
        :max-hour="20"
      />
    </demo-block>

    <demo-block card :title="t('datetimeType')">
      <van-datetime-picker
        v-model="value.datetime"
        type="datetime"
        :title="t('datetimeType')"
        :min-date="minDate"
        :max-date="maxDate"
      />
    </demo-block>

    <demo-block v-if="!isWeapp" card :title="t('datehourType')">
      <van-datetime-picker
        v-model="value.datehour"
        type="datehour"
        :title="t('datehourType')"
        :min-date="minDate"
        :max-date="maxDate"
      />
    </demo-block>

    <demo-block card :title="t('optionFilter')">
      <van-datetime-picker
        v-model="value.optionFilter"
        type="time"
        :title="t('optionFilter')"
        :filter="filter"
      />
    </demo-block>

    <demo-block v-if="!isWeapp" card :title="t('sortColumns')">
      <van-datetime-picker
        v-model="value.sortColumnsDate"
        type="date"
        :title="t('sortColumns')"
        :columns-order="['month', 'day', 'year']"
        :min-date="minDate"
        :max-date="maxDate"
        :formatter="formatter"
      />
    </demo-block>
  </demo-section>
</template>

<script>
export default {
  i18n: {
    'zh-CN': {
      day: '???',
      year: '???',
      month: '???',
      timeType: '????????????',
      dateType: '???????????????',
      datetimeType: '??????????????????',
      datehourType: '?????????????????????',
      monthDayType: '????????????',
      yearMonthType: '????????????',
      optionFilter: '???????????????',
      sortColumns: '??????????????????',
    },
    'en-US': {
      day: ' Day',
      year: ' Year',
      month: ' Month',
      timeType: 'Choose Time',
      dateType: 'Choose Date',
      datetimeType: 'Choose DateTime',
      datehourType: 'Choose DateHour',
      monthDayType: 'Choose Month-Day',
      yearMonthType: 'Choose Year-Month',
      optionFilter: 'Option Filter',
      sortColumns: 'Columns Order',
    },
  },

  data() {
    return {
      minDate: new Date(2020, 0, 1),
      maxDate: new Date(2025, 10, 1),
      value: {
        date: new Date(2021, 0, 17),
        time: '12:00',
        datetime: new Date(2020, 0, 1),
        datehour: new Date(2020, 0, 1),
        monthDay: new Date(2020, 0, 1),
        yearMonth: new Date(2020, 0, 1),
        optionFilter: '12:00',
        sortColumnsDate: new Date(2020, 0, 1),
      },
    };
  },

  methods: {
    formatter(type, value) {
      if (type === 'year') {
        return value + this.t('year');
      }
      if (type === 'month') {
        return value + this.t('month');
      }
      if (type === 'day') {
        return value + this.t('day');
      }
      return value;
    },

    filter(type, values) {
      if (type === 'minute') {
        return values.filter((value) => value % 5 === 0);
      }

      return values;
    },
  },
};
</script>
