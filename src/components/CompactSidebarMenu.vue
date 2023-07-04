<script lang="ts">
import IconBuilding from "./icons/IconBuilding.vue";
import IconBook from "./icons/IconBook.vue";
import IconNewsAllRead from "./icons/IconNewsAllRead.vue";
import IconPassword from "./icons/IconPassword.vue";
import IconSettings from "./icons/IconSettings.vue";
import IconTime from "./icons/IconTime.vue";
import PopoverContent from "./PopoverContent.vue";
export default {
  name: "CompactSidebarMenu",
  components: {
    IconBuilding: IconBuilding,
    IconBook: IconBook,
    IconNewsAllRead: IconNewsAllRead,
    IconPassword: IconPassword,
    IconSettings: IconSettings,
    IconTime: IconTime,
    PopoverContent: PopoverContent,
  },
  props: {
    unreadMessages: {
      type: Number,
      required: true,
    },
    showFullSidebarMenu: {
      type: Function,
      required: true,
    },
    customRightPopper: {
      type: String,
      required: true,
    },
    customPopover: {
      type: String,
      required: true,
    },
  },
  data() {
    return {};
  },
};
</script>

<template>
  <el-aside width="60px" class="sidebar">
    <div class="wrapper">
      <el-tooltip
        placement="right"
        content="Развернуть"
        :popper-class="customRightPopper"
      >
        <el-button class="custom-button" @click="showFullSidebarMenu">
          <IconBuilding />
        </el-button>
      </el-tooltip>
      <div>
        <el-tooltip
          placement="right"
          content="График работы"
          :popper-class="customRightPopper"
        >
          <el-button class="custom-button">
            <IconBook />
          </el-button>
        </el-tooltip>
      </div>
      <el-badge
        v-if="unreadMessages > 0"
        is-dot
        class="custom-badge"
        is-fixed="false"
      >
        <el-tooltip
          placement="right"
          content="Новости компании"
          :popper-class="customRightPopper"
        >
          <el-button class="custom-button">
            <IconNewsAllRead />
          </el-button>
        </el-tooltip>
      </el-badge>
      <el-tooltip
        v-else
        placement="right"
        content="Новости компании"
        :popper-class="customRightPopper"
      >
        <el-button class="custom-button">
          <IconNewsAllRead />
        </el-button>
      </el-tooltip>
      <div>
        <el-tooltip
          placement="right"
          content="База знаний"
          :popper-class="customRightPopper"
        >
          <el-button class="custom-button">
            <IconPassword />
          </el-button>
        </el-tooltip>
      </div>
      <div>
        <el-tooltip
          placement="right"
          content="Пароли"
          :popper-class="customRightPopper"
        >
          <el-button class="custom-button">
            <IconTime />
          </el-button>
        </el-tooltip>
      </div>
    </div>
    <el-tooltip
      placement="right"
      content="Настройки"
      :popper-class="customRightPopper"
    >
      <el-popover
        placement="right"
        :visible-arrow="false"
        :popper-class="customPopover"
      >
        <PopoverContent />
        <el-button slot="reference" class="custom-button__settings">
          <IconSettings />
        </el-button>
      </el-popover>
    </el-tooltip>
  </el-aside>
</template>
