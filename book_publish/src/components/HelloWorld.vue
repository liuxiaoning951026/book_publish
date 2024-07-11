<template>
  <div class="hello">
    <div class="container">
      <el-descriptions title="书号查询" :column="2" border>
        <template slot="extra">
          <el-button type="primary" size="small" icon="el-icon-upload"
            >上传</el-button
          >
        </template>

        <el-descriptions-item label="出版社">
          <el-input v-model="input1" placeholder="请输入内容"></el-input>
        </el-descriptions-item>
        <el-descriptions-item
          label="时间"
          :contentStyle="{ 'text-align': 'center' }"
        >
          <el-date-picker
            v-model="timeStr"
            type="datetime"
            placeholder="选择日期时间"
            style="width: 100%"
          >
          </el-date-picker
        ></el-descriptions-item>

        <el-descriptions-item label="">
          <template slot="label">
            <el-input
              v-model="input3"
              placeholder="请输入名称"
              style="flex: 1; margin-right: 12px"
            ></el-input>
          </template>
          <div style="display: flex">
            <el-input
              v-model="input2"
              placeholder="请输入内容"
              style="flex: 1; margin-right: 12px"
            ></el-input>
            <el-button type="primary" size="small" icon="el-icon-search"
              >查询</el-button
            >
          </div>
        </el-descriptions-item>
      </el-descriptions>

      <el-descriptions :column="2" border>
        <template slot="title">
          <span>2024年{{ input1 }}线上审稿系统</span></template
        >
        <el-descriptions-item label="姓名">
          <el-input v-model="input4" placeholder="请输入内容"></el-input>
        </el-descriptions-item>
        <el-descriptions-item label="性别">
          <el-select
            v-model="selectAex"
            placeholder="请选择性别"
            style="width: 100%"
          >
            <el-option key="1" label="男" value="1"> </el-option>
            <el-option key="2" label="女" value="2"> </el-option>
          </el-select>
        </el-descriptions-item>

        <el-descriptions-item label="证件类型">
          <el-select
            v-model="selectCardType"
            placeholder="请选择证件类型"
            style="width: 100%"
          >
            <el-option key="1" label="居民身份证" value="1"> </el-option>
            <el-option key="2" label="护照" value="2"> </el-option>
            <el-option key="3" label="驾驶证" value="3"> </el-option>
            <el-option key="4" label="居住证" value="4"> </el-option>
          </el-select>
        </el-descriptions-item>
        <el-descriptions-item label="总数字">
          <el-input v-model="input5" placeholder="请输入内容"></el-input>
        </el-descriptions-item>

        <el-descriptions-item label="选题名称">
          <el-input v-model="input6" placeholder="请输入内容"></el-input>
        </el-descriptions-item>
        <el-descriptions-item label="作品上传">
          <el-select
            v-model="selectUploadStatus"
            placeholder="请选择上传进度"
            style="width: 100%"
          >
            <el-option key="1" label="未上传" value="1"> </el-option>
            <el-option key="2" label="已上传" value="2"> </el-option
          ></el-select>
        </el-descriptions-item>

        <el-descriptions-item label="评审进度">
          <el-select
            v-model="selectReviewStatus"
            placeholder="请选择评审进度"
            style="width: 100%"
          >
            <el-option key="1" label="未评审" value="1"> </el-option>
            <el-option key="2" label="评审中" value="2"> </el-option>
            <el-option key="3" label="评审失败" value="3"> </el-option>
            <el-option key="4" label="未完成" value="4"> </el-option>
            <el-option key="5" label="已完成" value="5"> </el-option
          ></el-select>
        </el-descriptions-item>
        <el-descriptions-item label="评审结果">
          <el-input v-model="input7" placeholder="请输入内容"></el-input>
        </el-descriptions-item>
      </el-descriptions>

      <div class="btns">
        <el-button @click="resetForm">重置</el-button>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "HelloWorld",
  data() {
    return {
      input1: "",
      input2: "",
      input3: "",
      input4: "",
      input5: "",
      input6: "",
      input7: "",
      timeStr: "",
      selectAex: "",
      selectUploadStatus: "",
      selectReviewStatus: "",
      selectCardType: "",
    };
  },
  methods: {
    resetForm() {
      this.input1 = "";
      this.input2 = "";
      this.input3 = "";
      this.input4 = "";
      this.input5 = "";
      this.input6 = "";
      this.input7 = "";
      this.timeStr = "";
      this.selectAex = "";
      this.selectUploadStatus = "";
      this.selectReviewStatus = "";
      this.selectCardType = "";
    },
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style>
.hello {
  width: 100%;
  height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
}
.container {
  border: 1px solid #ebebeb;
  height: 50%;
  width: 50%;
}
.el-descriptions__header {
  line-height: 50px;
  margin-bottom: 0px;
  padding-left: 16px;
  padding-right: 16px;
  background: #fafafa;
}

.btns {
  width: 100%;
  display: flex;
  justify-content: end;
  margin-top: 24px;
}
</style>
