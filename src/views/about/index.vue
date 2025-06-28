<template>
  <div>
    <div class="card mb10">
      <h4 class="title">简介</h4>
      <span class="text">
        <el-link type="primary" href="https://github.com/chenbin0702/cms-admin" target="_blank">CMS-Admin</el-link>，一个基于 Vue
        3、TypeScript 和 Element-Plus
        的企业级内容管理系统，致力于为您提供一个流畅、直观且功能强大的内容管理平台。它不仅融合了最新的技术趋势，而且通过精心设计，确保了系统的简洁性和高效，让企业可以专注于内容运营和管理。
      </span>
    </div>
    <div class="card mb10">
      <h4 class="title">项目信息</h4>
      <el-descriptions :column="2" border>
        <el-descriptions-item label="版本号" label-align="left">
          <el-tag>v{{ version }}</el-tag>
        </el-descriptions-item>
        <el-descriptions-item label="作者" label-align="left">
          <el-tag> CMS-Admin Team </el-tag>
        </el-descriptions-item>
        <el-descriptions-item label="GitHub仓库" label-align="left" :span="2">
          <el-link type="primary" href="https://github.com/chenbin0702/cms-admin" target="_blank"> Github: cms-admin </el-link>
        </el-descriptions-item>
      </el-descriptions>
    </div>
  </div>
</template>

<script setup lang="ts" name="about">
const version: string = __APP_VERSION__;
</script>

<style lang="scss" scoped>
.card {
  .title {
    margin: 0 0 15px;
    font-size: 17px;
    font-weight: bold;
    color: var(--el-text-color-primary);
  }
  .text {
    font-size: 15px;
    line-height: 25px;
    color: var(--el-text-color-regular);
    .el-link {
      font-size: 15px;
    }
  }

  /* 添加 Markdown 内容样式 */
  [v-html] {
    padding: 1em;
    background: #f9f9f9;
    border-radius: 5px;
    line-height: 1.6;
    font-size: 14px;
    color: #333;
  }

  [v-html] h1,
  [v-html] h2,
  [v-html] h3 {
    border-bottom: 1px solid #ddd;
    padding-bottom: 0.3em;
    margin-bottom: 0.5em;
    color: #333;
  }

  [v-html] pre {
    background: #f3f3f3;
    padding: 1em;
    border-radius: 5px;
    overflow-x: auto;
  }

  [v-html] code {
    background: #f3f3f3;
    padding: 0.2em 0.4em;
    border-radius: 3px;
  }
}
</style>
