<template>
  <div class="addindentityjie">
    <p>
      <span>给身份设置api接口权限</span>
    </p>
    <p>
      <el-select v-model="identity_id" placeholder="请选择身份id">
        <el-option
          v-for="(item,index) in identity"
          :key="index"
          :label="item.identity_text"
          :value="item.identity_id"
        >{{item.identity_text}}</el-option>
      </el-select>
    </p>
    <p>
      <el-select v-model="api_authority_id" placeholder="请选择api接口权限">
        <el-option
          v-for="(item,index) in apiauthorityFn"
          :key="index"
          :label="item.api_authority_text"
          :value="item.identity_api_authority_relation_id"
        >{{item.api_authority_text}}</el-option>
      </el-select>
    </p>
    <p>
      <el-button type="primary" @click="okFn">确定</el-button>
      <el-button @click="resetFn">重置</el-button>
    </p>
  </div>
</template>
<script>
import { mapState } from "vuex";
import api from "../../../../api/index";
export default {
  props: {},
  components: {},
  data() {
    return {
      identity_id: "",
      api_authority_id: ""
    };
  },
  computed: {
    ...mapState(["identity", "apiauthorityFn"])
  },
  methods: {
    resetFn() {
      this.identity_id = "";
      this.api_authority_id = "";
    },
    okFn() {
      if (this.identity_id !== "" && this.api_authority_id !== "") {
        api.userSetIdentityApi({
          identity_id: this.identity_id,
          api_authority_id: this.api_authority_id
        });
      } else {
        alert("不能为空哦，亲爱滴");
      }
    }
  },
  created() {},
  mounted() {}
};
</script>
<style scoped lang="scss">
.addindentityjie {
  width: 100%;
  padding: 10px;
  box-sizing: border-box;
  border: 1px solid #ccc;
  border-radius: 10px;
  p {
    margin: 6px;
    span {
      border: 1px solid #00f;
      color: #00f;
      padding: 3px 10px;
      margin-right: 10px;
      background: #fff;
    }
  }
}
</style>
