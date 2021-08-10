<!--  -->
<template>
  <div class="chat-wrap">
    <el-card class="chat-box">
      <div class="header">
        <template v-for="item in info">
          <div class="left" :key="item.id" v-if="item.self===0">
            <div class="name" style="margin-right: 10px">{{ item.name }}</div>
            <div>{{ item.message }}</div>
          </div>
          <div class="right" :key="item.id" v-else>
            <div style="padding-right: 10px">{{ item.message }}</div>
            <div class="name">临汾</div>
          </div>
        </template>
      </div>
      <div class="center">
        <div title="表情" style="cursor: pointer">
          😀
        </div>
      </div>
      <div class="footer">
        <div class="enter" contentEditable="true" ref="contentEditable"></div>
        <div class="btn">
          <el-button type="primary" size="small" @click="sendAction">发送</el-button>
        </div>
      </div>
    </el-card>

  </div>
</template>

<script>
const info = [
  {
    id:1,
    self:0,
    name:'杨东',
    type:1, // 1.代表文字
    message:'你好，很高兴认识你'
  }
]
export default {
  data:()=> ({
    info
  }),

  components: {

  },

  mounted() {

  },

  methods: {
    sendAction(){
      let oBox = this.$refs.contentEditable
      let value =oBox.innerHTML
      let message = {
        id:Date.now(),
        self:1,
        name:'杨东',
        type:1, // 1.代表文字
        message:value
      }
      this.info.push(message)
      console.log(value)
      oBox.innerHTML = ''
    }
  }
}

</script>
<style rel='stylesheet/scss' lang='scss' scoped>
::v-deep{
  .el-card__body{
    padding: 0;
  }
}
.chat-wrap{
  width: 100%;
  height: 100%;
}
.chat-box{
  width: 50%;
  height: calc(100vh - 61px);
  .header{
    padding: 15px;
    font-size: 12px;
    width: 100%;
    height: 400px;
    border-bottom: 1px solid #EBEEF5;
    .name{
      color: white;
      width: 30px;
      border-radius: 4px;
      height: 30px;
      display: flex;
      font-size: 12px;
      align-items: center;
      justify-content: center;
      background: #409EFF;

    }
    .left{
      display: flex;
      align-items: center;
      margin-bottom: 10px;
    }
    .right{
      margin-bottom: 10px;
      display: flex;
      align-items: center;
      justify-content: flex-end;
    }
  }
  .center{
    height: 40px;
    border-bottom: 1px solid #EBEEF5;
    display: flex;
    align-items: center;
  }
  .footer{
    .enter{
      padding: 10px;
      height: 100px;
      overflow: auto;
      border-bottom: 1px solid #EBEEF5;
    }
  }
  .btn{
    display: flex;
    justify-content: flex-end;
  }

}
</style>