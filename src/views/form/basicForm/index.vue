<template>
  <!-- hidden PageHeaderWrapper title demo -->
  <page-header-wrapper :title="false" :content="$t('form.basic-form.basic.description')">
    <a-card :body-style="{ padding: '24px 32px' }" :bordered="false">
      <a-form @submit="handleSubmit" :form="form">
        <a-form-item
          label="日期"
          :labelCol="{ lg: { span: 7 }, sm: { span: 7 } }"
          :wrapperCol="{ lg: { span: 10 }, sm: { span: 17 } }"
        >
          <a-range-picker
            name="buildTime"
            style="width: 100%"
            v-decorator="['buildTime', { rules: [{ required: true, message: '请选择日期' }] }]"
          />
        </a-form-item>
        <a-form-item
          label="日期"
          :labelCol="{ lg: { span: 7 }, sm: { span: 7 } }"
          :wrapperCol="{ lg: { span: 10 }, sm: { span: 17 } }"
        >
          <a-cascader :options="options" placeholder="Please select" @change="onChange" />
        </a-form-item>
        <a-form-item :wrapperCol="{ span: 24 }" style="text-align: center">
          <a-button htmlType="submit" type="primary">提交</a-button>
          <a-button style="margin-left: 8px">取消</a-button>
        </a-form-item>
      </a-form>
    </a-card>
  </page-header-wrapper>
</template>

<script>
export default {
  name: 'BaseForm',
  data () {
    return {
      form: this.$form.createForm(this)
    }
  },
  methods: {
    handleSubmit (e) {
      e.preventDefault()
      this.form.validateFields((err, values) => {
        if (!err) {
          console.log('Received values of form: ', values)
        }
      })
    }
  }
}
</script>
