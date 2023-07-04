<script lang="ts">
import IconAbsenseList from "./icons/IconAbsenseList.vue";
import IconDealsDistribution from "./icons/IconDealsDistribution.vue";
import IconEmloyees from "./icons/IconEmloyees.vue";
export default {
  name: "PopoverContent",
  components: {
    IconAbsenseList: IconAbsenseList,
    IconDealsDistribution: IconDealsDistribution,
    IconEmloyees: IconEmloyees,
  },
  data() {
    return {};
  },
};
</script>

<template>
  <div class="custom-popover-wrapper">
    <div class="sidebar-item">
      <el-button
        class="custom-button custom-button__full custom-button__full-default"
      >
        <div class="sidebar-button__content">
          <IconEmloyees />
          <span class="sidebar-item__title">Сотрудники</span>
        </div>
      </el-button>
    </div>
    <div class="sidebar-item">
      <el-button
        class="custom-button custom-button__full custom-button__full-default"
      >
        <div class="sidebar-button__content">
          <IconAbsenseList />
          <span class="sidebar-item__title">Список отсутствий</span>
        </div>
      </el-button>
    </div>
    <div class="sidebar-item">
      <el-button
        class="custom-button custom-button__full custom-button__full-default"
      >
        <div class="sidebar-button__content">
          <IconDealsDistribution />
          <span class="sidebar-item__title">Распределение сделок</span>
        </div>
      </el-button>
    </div>
  </div>
</template>

<style>
.custom-popover-wrapper {
  width: 100%;
}
</style>
