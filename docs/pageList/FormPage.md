##### FormPage

展示如下图
![formPage](../image/formPageImage.png)

| name         | type    | default | Description                                |
| ------------ | ------- | ------- | ------------------------------------------ |
| type         | string  |         | from(普通表单)\dialogform(弹窗表单)        |
| status       | string  |         | add 为 type = dialogform 出现连续添加按钮  |
| isContinuous | boolean |         | true 为 type = dialogform 出现连续添加按钮 |
| title        | string  |         | type = dialogform 标题                     |
| width        | string  |         | type = dialogform 宽度                     |
| form         | object  |         | 内部表单配置信息                           |

---

- 使用方式 `触发事件同gridPage一样`

```javascript
import FormPage from "@/components/Page/FormPage.vue";

// components 注册子组件

      <FormPage
      :options="pageOptions"
      @onFieldChange="onFieldChange"
      @onButtonClick="onButtonClick"
      @onFieldVisibleChange="onFieldVisibleChange"
      ref="formPage"
    ></FormPage>
```

---

- 如果作为详情页面

```javascript
// 作为详情页面，参数回绑

// 例子：res为接口返回值

//1.formData  对应绑定到form配置的group里的prop字段
this.pageOptions.form.formData = res;

//2.单个回绑
this.pageOptions.form.formData.name = res.name;
this.$set(this.pageOptions.form.formData, "name", res.name); // 强制更新
```

---

- form 配置信息

| name                       | type    | default | Description                                                   |
| -------------------------- | ------- | ------- | ------------------------------------------------------------- |
| ref                        | string  |         | 组件标识，ref 作用                                            |
| direction                  | string  |         | 布局方式 vertical\horizontal                                  |
| width                      | string  |         | form 组件宽度 如"25%"                                         |
| elementWidth               | string  |         | 控件（输入框）宽度 如"25%"                                    |
| labelWidth                 | string  |         | label 宽度 如"25%"                                            |
| formData                   | object  |         | 对应 group 配置的参数字段                                     |
| disabled                   | boolean |         | 是否禁用所有的输入框                                          |
| group                      | array   |         | 控件分组配置                                                  |
| buttonGroupGridSumbitStyle | string  |         | 底部配置按钮样式（可调整底部按钮位置） 如'text-align:center;' |
| buttonGroupGridSumbit      | Array   |         | 底部配置按钮配置                                              |
| buttonGroupStyle           | string  |         | 配置右上角按钮样式 如'text-align:center;'                     |
| buttonGroup                | Array   |         | 固定表单右上角按钮                                            |



