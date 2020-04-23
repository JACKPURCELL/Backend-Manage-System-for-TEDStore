<template>
  <a-card :body-style="{padding: '24px 32px'}" :bordered="false">
    <a-form @submit="handleSubmit" :form="form">
      <a-form-item
        label="_chunkingType"
        :labelCol="{lg: {span: 7}, sm: {span: 7}}"
        :wrapperCol="{lg: {span: 10}, sm: {span: 17} }">
        <a-radio-group
          v-decorator="['chunkingType', { initialValue: chunkingType }]"
          buttonStyle="solid">
          <a-radio-button value="0">
            Fixed
          </a-radio-button>
          <a-radio-button value="1">
            Variable
          </a-radio-button>
        </a-radio-group>
      </a-form-item>
      <a-form-item
        label="_minChunkSize"
        :labelCol="{lg: {span: 7}, sm: {span: 7}}"
        :wrapperCol="{lg: {span: 10}, sm: {span: 17} }">
        <a-row>
          <a-col :span="12">
            <a-slider v-decorator="['minChunkSize', { initialValue: minChunkSize }]" :min="1" :max="16384" />
          </a-col>
          <a-col :span="4">
            <a-input-number v-decorator="['minChunkSize', { initialValue: minChunkSize }]" :min="1" :max="16384" style="marginLeft: 16px" />
          </a-col>
        </a-row>
      </a-form-item>
      <a-form-item
        label="_avgChunkSize"
        :labelCol="{lg: {span: 7}, sm: {span: 7}}"
        :wrapperCol="{lg: {span: 10}, sm: {span: 17} }">
        <a-row>
          <a-col :span="12">
            <a-slider v-decorator="['avgChunkSize', { initialValue: avgChunkSize }]" :min="1" :max="16384" />
          </a-col>
          <a-col :span="4">
            <a-input-number v-decorator="['avgChunkSize', { initialValue: avgChunkSize }]" :min="1" :max="16384" style="marginLeft: 16px" />
          </a-col>
        </a-row>
      </a-form-item>
      <a-form-item
        label="_maxChunkSize"
        :labelCol="{lg: {span: 7}, sm: {span: 7}}"
        :wrapperCol="{lg: {span: 10}, sm: {span: 17} }">
        <a-row>
          <a-col :span="12">
            <a-slider v-decorator="['maxChunkSize', { initialValue: maxChunkSize }]" :min="1" :max="16384" />
          </a-col>
          <a-col :span="4">
            <a-input-number v-decorator="['maxChunkSize', { initialValue: maxChunkSize }]" :min="1" :max="16384" style="marginLeft: 16px" />
          </a-col>
        </a-row>
      </a-form-item>
      <a-form-item
        label="_slidingWinSize"
        :labelCol="{lg: {span: 7}, sm: {span: 7}}"
        :wrapperCol="{lg: {span: 10}, sm: {span: 17} }">
        <a-row>
          <a-col :span="12">
            <a-slider v-decorator="['slidingWinSize', { initialValue: slidingWinSize }]" :min="1" :max="1024" />
          </a-col>
          <a-col :span="4">
            <a-input-number v-decorator="['slidingWinSize', { initialValue: slidingWinSize }]" :min="1" :max="1024" style="marginLeft: 16px" />
          </a-col>
        </a-row>
      </a-form-item>
      <a-form-item
        label="_ReadSize"
        :labelCol="{lg: {span: 7}, sm: {span: 7}}"
        :wrapperCol="{lg: {span: 10}, sm: {span: 17} }">
        <a-row>
          <a-col :span="12">
            <a-slider v-decorator="['ReadSize', { initialValue: ReadSize }]" :min="1" :max="1024" />
          </a-col>
          <a-col :span="4">
            <a-input-number v-decorator="['ReadSize', { initialValue: ReadSize }]" :min="1" :max="1024" style="marginLeft: 16px" />
          </a-col>
        </a-row>
      </a-form-item>
      <a-form-item
        label="_keyBatchSize"
        :labelCol="{lg: {span: 7}, sm: {span: 7}}"
        :wrapperCol="{lg: {span: 10}, sm: {span: 17} }">
        <a-row>
          <a-col :span="12">
            <a-slider v-decorator="['keyBatchSize', { initialValue: keyBatchSize }]" :min="1" :max="10000" />
          </a-col>
          <a-col :span="4">
            <a-input-number v-decorator="['keyBatchSize', { initialValue: keyBatchSize }]" :min="1" :max="10000" style="marginLeft: 16px" />
          </a-col>
        </a-row>
      </a-form-item>
      <a-form-item
        label="_keyServerIP"
        :labelCol="{lg: {span: 7}, sm: {span: 7}}"
        :wrapperCol="{lg: {span: 7}, sm: {span: 17} }">
        <a-input
          v-decorator="[
            'keyServerIP',
            {rules: [{ required: false, message: 'keyServerIP' }]}
            , { initialValue: keyServerIP }]"/>
      </a-form-item>
      <a-form-item
        label="_keyServerPort"
        :labelCol="{lg: {span: 7}, sm: {span: 7}}"
        :wrapperCol="{lg: {span: 10}, sm: {span: 17} }">
        <a-row>
          <a-col :span="12">
            <a-slider v-decorator="['keyServerPort', { initialValue: keyServerPort }]" :min="1" :max="10000" />
          </a-col>
          <a-col :span="4">
            <a-input-number v-decorator="['keyServerPort', { initialValue: keyServerPort }]" :min="1" :max="10000" style="marginLeft: 16px" />
          </a-col>
        </a-row>
      </a-form-item>
      <a-form-item
        label="_sketchTableWidth"
        :labelCol="{lg: {span: 7}, sm: {span: 7}}"
        :wrapperCol="{lg: {span: 10}, sm: {span: 17} }">
        <a-row>
          <a-col :span="12">
            <a-slider v-decorator="['sketchTableWidth', { initialValue: sketchTableWidth }]" :min="1" :max="4194304" />
          </a-col>
          <a-col :span="4">
            <a-input-number v-decorator="['sketchTableWidth', { initialValue: sketchTableWidth }]" :min="1" :max="4194304" style="marginLeft: 16px" />
          </a-col>
        </a-row>
      </a-form-item>
      <a-form-item
        label="_optimalSolverComputeItemNumberThreshold"
        :labelCol="{lg: {span: 7}, sm: {span: 7}}"
        :wrapperCol="{lg: {span: 10}, sm: {span: 17} }">
        <a-row>
          <a-col :span="12">
            <a-slider v-decorator="['optimalSolverComputeItemNumberThreshold', { initialValue: optimalSolverComputeItemNumberThreshold }]" :min="1" :max="100000" />
          </a-col>
          <a-col :span="4">
            <a-input-number v-decorator="['optimalSolverComputeItemNumberThreshold', { initialValue: optimalSolverComputeItemNumberThreshold }]" :min="1" :max="100000" style="marginLeft: 16px" />
          </a-col>
        </a-row>
      </a-form-item>
      <a-form-item
        label="_storageBlowPercent"
        :labelCol="{lg: {span: 7}, sm: {span: 7}}"
        :wrapperCol="{lg: {span: 10}, sm: {span: 17} }">
        <a-row>
          <a-col :span="12">
            <a-slider v-decorator="['storageBlowPercent', { initialValue: storageBlowPercent }]" :min="0.001" :max="0.1" :step="0.001" />
          </a-col>
          <a-col :span="4">
            <a-input-number v-decorator="['storageBlowPercent', { initialValue: storageBlowPercent }]" :min="0.001" :max="0.1" :step="0.001" style="marginLeft: 16px" />
          </a-col>
        </a-row>
      </a-form-item>
      <a-form-item
        label="_storageServerIP"
        :labelCol="{lg: {span: 7}, sm: {span: 7}}"
        :wrapperCol="{lg: {span: 7}, sm: {span: 17} }">
        <a-input
          v-decorator="[
            'storageServerIP',
            {rules: [{ required: false, message: 'storageServerIP' }]}
            , { initialValue: storageServerIP }]"/>
      </a-form-item>
      <a-form-item
        label="storageServerPort"
        :labelCol="{lg: {span: 7}, sm: {span: 7}}"
        :wrapperCol="{lg: {span: 10}, sm: {span: 17} }">
        <a-row>
          <a-col :span="12">
            <a-slider v-decorator="['storageServerPort', { initialValue: storageServerPort }]" :min="1" :max="10000" />
          </a-col>
          <a-col :span="4">
            <a-input-number v-decorator="['storageServerPort', { initialValue: storageServerPort }]" :min="1" :max="10000" style="marginLeft: 16px" />
          </a-col>
        </a-row>
      </a-form-item>
      <a-form-item
        label="_maxContainerSize"
        :labelCol="{lg: {span: 7}, sm: {span: 7}}"
        :wrapperCol="{lg: {span: 10}, sm: {span: 17} }">
        <a-row>
          <a-col :span="12">
            <a-slider v-decorator="['maxContainerSize', { initialValue: maxContainerSize }]" :min="1" :max="8388608" />
          </a-col>
          <a-col :span="4">
            <a-input-number v-decorator="['maxContainerSize', { initialValue: maxContainerSize }]" :min="1" :max="8388608" style="marginLeft: 16px" />
          </a-col>
        </a-row>
      </a-form-item>
      <a-form-item
        label="_RecipeRootPath"
        :labelCol="{lg: {span: 7}, sm: {span: 7}}"
        :wrapperCol="{lg: {span: 7}, sm: {span: 17} }">
        <a-input
          v-decorator="[
            'RecipeRootPath',
            {rules: [{ required: false, message: 'RecipeRootPath' }]}
            , { initialValue: RecipeRootPath }]"/>
      </a-form-item>
      <a-form-item
        label="_containerRootPath"
        :labelCol="{lg: {span: 7}, sm: {span: 7}}"
        :wrapperCol="{lg: {span: 7}, sm: {span: 17} }">
        <a-input
          v-decorator="[
            'containerRootPath',
            {rules: [{ required: false, message: 'containerRootPath' }]}
            , { initialValue: containerRootPath }]"/>
      </a-form-item>
      <a-form-item
        label="_fp2ChunkDBName"
        :labelCol="{lg: {span: 7}, sm: {span: 7}}"
        :wrapperCol="{lg: {span: 7}, sm: {span: 17} }">
        <a-input
          v-decorator="[
            'fp2ChunkDBName',
            {rules: [{ required: false, message: 'fp2ChunkDBName' }]}
            , { initialValue: fp2ChunkDBName }]"/>
      </a-form-item>
      <a-form-item
        label="fp2MetaDBame"
        :labelCol="{lg: {span: 7}, sm: {span: 7}}"
        :wrapperCol="{lg: {span: 7}, sm: {span: 17} }">
        <a-input
          v-decorator="[
            'fp2MetaDBame',
            {rules: [{ required: false, message: 'fp2MetaDBame' }]}
            , { initialValue: fp2MetaDBame }]"/>
      </a-form-item>
      <a-form-item
        :wrapperCol="{ span: 24 }"
        style="text-align: center"
      >
        <a-button htmlType="submit" type="primary" @click="showModal">提交</a-button>
      </a-form-item>
    </a-form>
    <a-modal title="提交成功！" v-model="visible" @ok="handleOk">
      <p>你已成功提交配置信息</p>
      <p>Server已重启</p>
      <p>KeyManager已重启</p>
    </a-modal>
  </a-card>
</template>
<script src="https://unpkg.com/axios/dist/axios.min.js"></script>
<script>
import { axios } from '@/utils/request'

export default{
  name: 'BaseForm',
  data () {
    return {
      description: '请配置Server及Keymanager相关参数',
      chunkingType: '1',
      minChunkSize: 4096,
      avgChunkSize: 8192,
      maxChunkSize: 16384,
      slidingWinSize: 256,
      ReadSize: 128,
      keyBatchSize: 3000,
      keyServerIP: '127.0.0.1',
      keyServerPort: 6666,
      sketchTableWidth: 1048576,
      optimalSolverComputeItemNumberThreshold: 48000,
      storageBlowPercent: 0.005,
      storageServerIP: '127.0.0.1',
      storageServerPort: 6668,
      maxContainerSize: 8388608,
      RecipeRootPath: 'Recipes/',
      containerRootPath: 'Containers/',
      fp2ChunkDBName: 'db1',
      fp2MetaDBame: 'db2',
      visible: false,
      // form
      form: this.$form.createForm(this)

    }
  },
  methods: {
    showModal() {
      this.visible = true;
    },
    handleOk(e) {
      console.log(e);
      this.visible = false;
    },
    // handler
    handleSubmit (e) {
      e.preventDefault()
      this.form.validateFields((err, value) => {
        if (!err) {
          // eslint-disable-next-line no-console
          console.log('Received values of form: ', value)
          console.log('Received values of form: ', value.keyServerIP)
          if(value.chunkingType==='1'){
            value.chunkingType=1
          }else{
            value.chunkingType=0
          }
          var ChunkerConfig = {
             "_chunkingType": value.chunkingType,
             "_minChunkSize": value.minChunkSize,
             "_avgChunkSize": value.avgChunkSize,
             "_maxChunkSize": value.maxChunkSize,
             "_slidingWinSize": value.slidingWinSize,
             "_ReadSize": value.ReadSize
          }
          var KeyServerConfig= {
            "_keyBatchSize": value.keyBatchSize,
            "_keyServerIP": value.keyServerIP,
            "_keyServerPort": value.keyServerPort,
            "_sketchTableWidth": value.sketchTableWidth,
            "_optimalSolverComputeItemNumberThreshold": value.optimalSolverComputeItemNumberThreshold,
            "_storageBlowPercent": value.storageBlowPercent
          }
          var SPConfig= {
            "_storageServerIP": value.storageServerIP,
            "_storageServerPort": value.storageServerPort,
            "_maxContainerSize": value.maxContainerSize,
            "_RecipeRootPath": value.RecipeRootPath,
            "_containerRootPath": value.containerRootPath,
            "_fp2ChunkDBName": value.fp2ChunkDBName,
            "_fp2MetaDBame": value.fp2MetaDBame
          }
          var client= {
            "_clientID": 1,
            "_sendChunkBatchSize": 1000,
            "_sendRecipeBatchSize": 100000,
            "_sendShortHashMaskBitNumber": 12
          }
          var configjson={
            "ChunkerConfig": ChunkerConfig,
            "KeyServerConfig": KeyServerConfig,
            "SPConfig": SPConfig,
            "client":client
          }
        }
          console.log(configjson)
        axios({
            method:'post',
            url:'/form',
            data:configjson,
            headers:{'Content-Type': 'application/json'},
        }).then((res)=>{
            console.log(res.data)
            showModal();
        })
        // axios({
        //     method:'get',
        //     url:'/login',
        //     params:{
        //       username: "qqq",
        //       password:"abc",
        //     },
        //     // headers:{'Content-Type': 'application/json'},
        // }).then((res)=>{
        //     console.log("aaaaaa")
        //     console.log(res)
        //     showModal();
        // })
      })
    }
  }
}
</script>
