<template>
  <div class="hello" @click="clickPanel">
    <div class="container">
      <el-descriptions :column="2" border>
        <template slot="title">
          <span style="padding-left: 12px; border-left: 2px solid #64739d"
            >书号查询</span
          >
        </template>
        <template slot="extra">
          <el-button type="primary" size="small" icon="el-icon-upload"
            >上传</el-button
          >
        </template>

        <el-descriptions-item label="出版社">
          <el-input v-model.trim="input1" placeholder="请输入出版社"></el-input>
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
            class="timer"
          >
          </el-date-picker
        ></el-descriptions-item>

        <el-descriptions-item label="">
          <template slot="label">
            <el-input
              id="input-number-3"
              v-model.number="input3"
              placeholder="请输入总数"
              style="flex: 1; margin-right: 12px; width: 100%"
              @keyup.native="changeInput3Number($event)"
            ></el-input>
          </template>
          <div
            style="
              display: flex;
              width: 100%;
              justify-content: space-between;
              align-items: center;
            "
          >
            <el-input
              v-show="!isShowText"
              id="input-number-2"
              v-model.number="input2"
              placeholder="请输入已申请书号数量"
              style="flex: 1; margin-right: 12px; width: 100%"
              @keyup.native="changeInput2Number($event)"
            ></el-input>

            <div v-show="isShowText" @click.self.stop="clickText">
              书号：{{ input3 }} &nbsp;&nbsp; 已申请书号：{{
                input2
              }}
              &nbsp;&nbsp; 剩余书号：<span
                style="color: #409eff; font-size: 16px"
                >{{ input3 - input2 < 0 ? "0" : input3 - input2 }}</span
              >
            </div>
            <el-button type="primary" size="small" icon="el-icon-search"
              >查询</el-button
            >
          </div>
        </el-descriptions-item>
      </el-descriptions>

      <el-descriptions :column="2" border class="des-2">
        <template slot="title">
          <span style="padding-left: 12px; border-left: 2px solid #64739d"
            >2024年{{ input1 }}线上审稿系统</span
          ></template
        >
        <el-descriptions-item label="">
          <template slot="label">
            <span class="nameStr">姓名</span>
          </template>
          <el-input v-model.trim="input4" placeholder="请输入姓名"></el-input>
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
          <el-input v-model.trim="input5" placeholder="请输入总数字"></el-input>
        </el-descriptions-item>

        <el-descriptions-item label="">
          <template slot="label">
            <span class="nameStr">选题名称</span>
          </template>
          <el-input
            v-model.trim="input6"
            placeholder="请输入选题名称"
          ></el-input>
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
          <el-input
            v-model.trim="input7"
            placeholder="请输入评审结果"
          ></el-input>
        </el-descriptions-item>
      </el-descriptions>

      <div class="btns">
        <el-button @click="resetForm" size="small">重置</el-button>
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
      input8: "",
      input9: "",
      timeStr: "",
      selectAex: "",
      selectUploadStatus: "",
      selectReviewStatus: "",
      selectCardType: "",
      isShowText: false,
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
      this.input8 = "";
      this.timeStr = "";
      this.selectAex = "";
      this.selectUploadStatus = "";
      this.selectReviewStatus = "";
      this.selectCardType = "";
      this.isShowText = false;
    },

    blur() {
      this.isShowText = true;
    },

    focus() {
      this.isShowText = !this.isShowText;
      console.log("isShowText===", this.isShowText);
    },

    changeInput3Number(e) {
      let num = e.target.value;
      // 只允许输入数字
      this.input3 = num.replace(/\D/g, "");
    },

    changeInput2Number(e) {
      let num = e.target.value;
      // 只允许输入数字
      this.input2 = num.replace(/\D/g, "");
    },
    clickText() {
      console.log("dfsd");
      this.isShowText = !this.isShowText;
    },

    clickPanel(e) {
      // const inputNumber3 = document.getElementById("input-number-3"); // 当前元素
      const inputNumber2 = document.getElementById("input-number-2"); // 当前元素
      console.log(inputNumber2.contains(e.target));
      if (!inputNumber2.contains(e.target)) {
        this.isShowText = !this.isShowText;
      }
      // if (!this.isShowText) {
      //   this.isShowText = true
      // }
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
  height: auto;
  width: 90%;
  padding: 24px;
  display: flex;
  flex-direction: column;
  overflow-y: auto;
  border-radius: 5px;
}
.el-descriptions__header {
  line-height: 50px;
  margin-bottom: 0px;
  padding-left: 16px;
  padding-right: 16px;
  background: #fafafa;
  border: 1px solid #ebebeb;
  border-bottom: none;
}

.el-descriptions__title {
  font-size: 15px;
  font-weight: 600;
}

.btns {
  width: 100%;
  display: flex;
  justify-content: end;
  margin-top: 24px;
}

.el-input__inner {
  height: 32px;
  line-height: 32px;
}

.el-input__icon {
  line-height: 32px;
}
.el-descriptions-item__label.is-bordered-label {
  background: #ffffff;
}
.des-2 {
  .el-descriptions__header {
    border-top: none;
  }
}

.el-descriptions-item__label.is-bordered-label {
  color: #000000;
}
.nameStr::before {
  content: "*";
  color: #f56c6c;
  margin-right: 4px;
}
.el-input-number__decrease {
  width: 32px;
}
.el-input-number {
  line-height: 30px;
}
</style>
