<template>
  <div class="PeriodCard">
    <div class="PeriodCard-NumberBlock">
      <div class="PeriodCard-Number">
        <span class="PeriodCard-Number-Num">1</span>
        <span class="PeriodCard-Number-Text">時間目</span>
      </div>
      <div class="PeriodCard-Time">
        <span>00:00</span>
        <span>|</span>
        <span>00:00</span>
      </div>
    </div>
    <v-row>
      <v-col
        v-for="(item, i) in classData.getLessonsByDisplayDate"
        :key="i"
        cols="12"
        md="6"
      >
        <content-card
          :description="formatDate(item.startTime)"
          :title="item.content"
          :subjects="[{ name: item.subject }]"
        />
      </v-col>
    </v-row>
  </div>
</template>

<script lang="ts">
import Vue from 'vue'
import dayjs from 'dayjs'
import ContentCard from '@/components/ContentCard.vue'

export default Vue.extend({
  components: { ContentCard },
  props: {
    classData: {
      type: Object,
      default: () => {}
    }
  },
  methods: {
    formatDate(date: Date): string {
      return dayjs(date).format('HH:MM')
    }
  }
})
</script>

<style scoped lang="scss">
.PeriodCard {
  display: flex;
  border-bottom: 1px solid $color-base-color-02;
  padding-bottom: 12px;
  margin-bottom: 12px;

  &:last-child {
    border: none;
  }

  .PeriodCard-NumberBlock {
    display: flex;
    flex-direction: column;
    margin: 12px;
  }

  .PeriodCard-Number {
    display: flex;
    flex-direction: column;
    align-items: center;
    color: $color-white;
    background-color: $color-base-color-06;
    width: 40px;
    border-radius: 3em;
    padding: 12px 4px;
    margin-bottom: 8px;

    .PeriodCard-Number-Num {
      font-size: 22px;
    }

    .PeriodCard-Number-Text {
      font-size: 8px;
      font-weight: bold;
    }
  }

  .PeriodCard-Time {
    display: flex;
    flex-direction: column;
    justify-content: center;
    text-align: center;
    font-size: 10px;
    color: $color-white;
  }
}
</style>
