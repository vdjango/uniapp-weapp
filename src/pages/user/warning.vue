<template>
  <view class="page-message">
    <view class="page-message--inner">
      <image
        class="page-message--icon"
        src="@/static/msg-warning.svg"
        mode="aspectFit"
        lazy-load
      ></image>
      <view class="page-message--title">{{ i18n.t('user.registerValidate') }}</view>
      <qui-button size="medium" @click="handleLoginClick">
        {{ i18n.t('user.backHome') }}
      </qui-button>
    </view>
  </view>
</template>

<script>
export default {
  methods: {
    handleLoginClick() {
      // #ifdef MP-WEIXIN
      this.$store.dispatch('session/logout').then(() => {
        uni.clearStorage();
        uni.redirectTo({
          url: `/pages/home/index`,
        });
      });
      // #endif
      // #ifdef H5
      this.$store.dispatch('session/logout').then(() => {
        uni.redirectTo({
          url: `/pages/home/index`,
        });
      });
      // #endif
    },
  },
};
</script>

<style lang="scss" scoped>
@import '@/styles/base/variable/global.scss';

.page-message {
  display: flex;
  align-items: center;
  justify-content: center;
  &--icon {
    height: 140rpx;
    margin: 140rpx 0 80rpx;
  }
  &--inner {
    position: relative;
    padding-bottom: 20rpx;
    margin-top: 140rpx;
    text-align: center;
  }
  &--title {
    max-width: 510rpx;
    margin: 0 auto 40rpx;
    font-size: $fg-f5;
    font-weight: bold;
    line-height: 45rpx;
    color: rgba(51, 51, 51, 1);
  }
}
</style>
