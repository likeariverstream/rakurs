<script lang="ts">
import IconBuilding from "./icons/IconBuilding.vue";
import IconBook from "./icons/IconBook.vue";
import IconNewsAllRead from "./icons/IconNewsAllRead.vue";
import IconPassword from "./icons/IconPassword.vue";
import IconSettings from "./icons/IconSettings.vue";
import IconTime from "./icons/IconTime.vue";
import IconDoubleArrow from "./icons/IconDoubleArrow.vue";
import PopoverContent from "./PopoverContent.vue";
import CompactSidebarMenu from "./CompactSidebarMenu.vue";
export default {
  name: "SidebarMenu",
  components: {
    IconBuilding: IconBuilding,
    IconBook: IconBook,
    IconNewsAllRead: IconNewsAllRead,
    IconPassword: IconPassword,
    IconSettings: IconSettings,
    IconTime: IconTime,
    IconDoubleArrow: IconDoubleArrow,
    PopoverContent: PopoverContent,
    CompactSidebarMenu: CompactSidebarMenu,
  },
  data() {
    return {
      customRightPopper: "custom-popper__right",
      customBottomPopper: "custom-popper__bottom",
      customTopPopper: "custom-popper__top",
      customPopover: "custom-popover-modal",
      unreadMessages: 12,
      isHide: true,
    };
  },
  methods: {
    showFullSidebarMenu() {
      return (this.isHide = false);
    },
    hideFullSidebarMenu() {
      return (this.isHide = true);
    },
  },
};
</script>

<template>
  <CompactSidebarMenu
    v-if="isHide"
    :unreadMessages="unreadMessages"
    :showFullSidebarMenu="showFullSidebarMenu"
    :customRightPopper="customRightPopper"
    :customPopover="customPopover"
  />
  <el-aside v-else width="264px" class="sidebar__full">
    <div class="sidebar-buttons__wrapper">
      <div class="sidebar-item">
        <IconBuilding />
        <h4 class="sidebar__title">КОМПАНИЯ</h4>
        <el-tooltip
          placement="bottom"
          content="Свернуть"
          :popper-class="customBottomPopper"
        >
          <el-button class="custom-button" @click="hideFullSidebarMenu">
            <IconDoubleArrow />
          </el-button>
        </el-tooltip>
      </div>
      <div class="wrapper wrapper__full">
        <div class="sidebar-item">
          <el-button class="custom-button custom-button__full">
            <div class="sidebar-button__content">
              <IconBook />
              <span class="sidebar-item__title">График работы</span>
            </div>
          </el-button>
        </div>
        <el-badge
          v-if="unreadMessages > 0"
          is-dot
          class="custom-badge custom-badge__full"
        >
          <el-button
            class="custom-button custom-button__full custom-button__full-default"
          >
            <div class="sidebar-button__content">
              <IconNewsAllRead />
              <span class="sidebar-item__title">Новости компании</span>
              <el-badge
                :value="unreadMessages"
                class="custom-badge__count"
              ></el-badge>
            </div>
          </el-button>
        </el-badge>
        <el-button
          v-else
          class="custom-button custom-button__full custom-button__full-default"
        >
          <div class="sidebar-button__content">
            <IconNewsAllRead />
            <span class="sidebar-item__title">Новости компании</span>
          </div>
        </el-button>
        <div class="sidebar-item">
          <el-button
            class="custom-button custom-button__full custom-button__full-default"
          >
            <div class="sidebar-button__content">
              <IconPassword />
              <span class="sidebar-item__title">База знаний</span>
            </div>
          </el-button>
        </div>
        <div class="sidebar-item">
          <el-button
            class="custom-button custom-button__full custom-button__full-default"
          >
            <div class="sidebar-button__content">
              <IconTime />
              <span class="sidebar-item__title">Пароли</span>
            </div>
          </el-button>
        </div>
      </div>
    </div>
    <div class="sidebar-item">
      <el-tooltip
        placement="top"
        content="Настройки"
        :popper-class="customTopPopper"
      >
        <el-popover
          placement="top"
          class="custom-popover"
          :visible-arrow="false"
          :popper-class="customPopover"
        >
          <PopoverContent />
          <el-button
            slot="reference"
            class="custom-button__settings custom-button__settings__full"
          >
            <div class="sidebar-button__content">
              <IconSettings />
              <span class="sidebar-item__title">Настройки</span>
            </div>
          </el-button>
        </el-popover>
      </el-tooltip>
    </div>
  </el-aside>
</template>

<style lang="scss">
.el-tooltip__popper {
  &.is-dark.custom-popper__right {
    display: flex;
    padding: 10px;
    align-items: center;
    gap: 10px;
    border-radius: 4px;
    box-sizing: border-box;
    background: var(--main-palette-primary-base, #17505b);

    & > div {
      border-right-color: var(--main-palette-primary-base, #17505b);
    }

    & > div::after {
      border-left-width: 0;
      border-right-color: var(--main-palette-primary-base, #17505b);
      left: 1px;
    }
  }

  &.is-dark.custom-popper__bottom {
    display: flex;
    padding: 10px;
    align-items: flex-start;
    gap: 10px;
    border-radius: 4px;
    box-sizing: border-box;
    background: var(--main-palette-primary-base, #17505b);

    & > div {
      border-bottom-color: var(--main-palette-primary-base, #17505b);
    }

    & > div::after {
      border-top-width: 0;
      border-bottom-color: var(--main-palette-primary-base, #17505b);
      left: 1px;
    }
  }

  &.is-dark.custom-popper__top {
    display: flex;
    padding: 10px;
    align-items: flex-start;
    gap: 10px;
    border-radius: 4px;
    box-sizing: border-box;
    background: var(--main-palette-primary-base, #17505b);

    & > div {
      border-top-color: var(--main-palette-primary-base, #17505b);
    }

    & > div::after {
      border-bottom-width: 0;
      border-top-color: var(--main-palette-primary-base, #17505b);
      left: 1px;
    }
  }
}

.el-button--default.custom-button {
  width: max-content;
  padding: 0;
  background: 0;
  border: none;
  display: flex;
  align-items: center;
  justify-content: center;
  margin: 0;

  & > span > svg {
    display: block;
  }

  &__full {
    width: 100%;
    justify-content: flex-start;
    padding: 8px 10px;
    gap: 10px;
    align-self: stretch;
    border-radius: 8px;
    background: var(--main-palette-success-border, #e2f5ea);

    &-default {
      background: none;
    }
  }
}

.el-button--default.custom-button__settings {
  display: flex;

  & > span > svg {
    display: block;
  }

  box-sizing: border-box;
  width: 32px;
  height: 32px;
  padding: 4px;
  display: flex;
  align-items: center;
  justify-content: center;
  margin: 0;

  &__full {
    width: 100%;
    display: flex;
    padding: 8px 10px;
    align-items: center;
    justify-content: flex-start;
    gap: 10px;
  }
}

.el-aside.sidebar {
  box-sizing: border-box;
  display: flex;
  padding-top: 16px;
  padding-bottom: 18px;
  position: fixed;
  left: 0;
  top: 0;
  width: 60px;
  height: 100vh;
  flex-direction: column;
  justify-content: space-between;
  align-items: center;
  border-right: 1px solid var(--main-palette-primary-border, #d1dcde);
  background: #ffffff;
}

.el-aside.sidebar__full {
  box-sizing: border-box;
  display: flex;
  padding: 16px 20px 10px;
  position: fixed;
  left: 0;
  top: 0;
  height: 100vh;
  flex-direction: column;
  justify-content: space-between;
  align-items: flex-start;
  border-right: 1px solid var(--main-palette-primary-border, #d1dcde);
  background: #ffffff;
}

.el-badge.custom-badge {
  position: relative;

  & > sup {
    top: 6px;
    left: 3px;
    width: 9px;
    height: 9px;
    background: var(--main-palette-success-base, #6fcf97);
  }

  &__full {
    width: 100%;

    & sup {
      top: 18px;
      left: 12px;
    }
  }

  &__count {
    & sup {
      border-radius: 10px;
      border: 1px solid var(--main-palette-success-base, #6fcf97);
      background: var(--main-palette-success-base, #6fcf97);
      color: var(--neutral-white, #fff);
      text-align: center;
      font-size: 12px;
      font-family: Roboto;
      font-style: normal;
      font-weight: 500;
      line-height: 18px;
    }
  }
}

.sidebar-buttons__wrapper {
  width: 100%;
}

.wrapper {
  width: 100%;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: space-between;
  gap: 16px;

  &__full {
    margin-top: 20px;
    width: 100%;
    gap: 0px;
    align-items: flex-start;
  }
}

.sidebar-item {
  min-width: 100%;
  display: flex;
  align-items: center;
  justify-content: space-between;
}

.sidebar-button__content {
  width: 100%;
  display: flex;
  align-items: center;
  gap: 10px;
  justify-content: space-between;
}

.sidebar__title {
  margin: 0 auto 0 0;
  color: #000;
  font-size: 24px;
  font-family: Roboto;
  font-style: normal;
  font-weight: 700;
  line-height: 100%;
  text-transform: uppercase;
}

.sidebar-item__title {
  color: #313942;
  font-size: 14px;
  font-family: Roboto;
  font-style: normal;
  font-weight: 500;
  line-height: 32px;
}

.custom-popover {
  width: 100%;

  &.el-popover__reference-wrapper {
    width: 100%;
  }
}

.custom-popover-modal {
  display: flex;
  flex-direction: column;
  align-items: flex-start;
  border-radius: 8px;
  padding: 0;
  border: 1px solid var(--main-palette-primary-base, #17505b);
  background: #fff;
  box-shadow: 0px 4px 4px 0px rgba(209, 220, 222, 0.5);
  border: 1px solid var(--main-palette-primary-base, #17505b);
  outline: #17505b;
}
</style>
