<template>
  <ScrollContainer>
    <div ref="wrapperRef" :class="prefixCls">
      <Tabs class="tabs">
        <template v-for="item in settingList" :key="item.key">
          <TabPane :tab="item.name">
            <component :is="item.component" />
          </TabPane>
        </template>
      </Tabs>
    </div>
  </ScrollContainer>
</template>

<script lang="ts">
  import { defineComponent } from 'vue';
  import { Tabs } from 'ant-design-vue';

  import { ScrollContainer } from '@/components/Container/index';
  import { settingList } from './data';

  import BaseSetting from './BaseSetting.vue';
  import SecureSetting from './SecureSetting.vue';
  import AccountBind from './AccountBind.vue';
  import OnlineDevice from './OnlineDevice.vue';
  import MsgNotify from './MsgNotify.vue';

  export default defineComponent({
    components: {
      ScrollContainer,
      Tabs,
      TabPane: Tabs.TabPane,
      BaseSetting,
      SecureSetting,
      AccountBind,
      MsgNotify,
      OnlineDevice,
    },
    setup() {
      return {
        prefixCls: 'account-setting',
        settingList,
      };
    },
  });
</script>
<style lang="less">
  .account-setting {
    margin: 12px;
    border-radius: 8px;
    background-color: @component-background;

    .base-title {
      padding-left: 10px;
    }
  }

  .tabs {
    padding-left: 10px;
  }
</style>
