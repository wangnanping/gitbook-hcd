#### group 配置详情

[`input`](#inputId) [`select`](#selectId) [`checkbox`](#checkboxId) [`span文字展示`](#spanId) [`cascader地区选择控件`](#cascaderId) [`select-tree树形下拉`](#select-treeId) [`upload图片上传`](#uploadId) [`datePicker时间控件`](#datePickerId) [`radio单选控件`](#radioId) [`右插槽`](#rightSlotId) [`提示信息ellipsis`](#ellipsisId) [`新增自定义span`](#setspanId) [`控件显示隐藏配置isShow`](#isShowId)

---

`标题配置`

```javascript
group: [
  //控件分组
  {
    title: "这是一组控件", //标题名称
    tooltipShow: boolean, //标题名称的提示显示 true false
    tooltipContent: "", //提示信息内容
    tooltipStyle: "", //提示图标样式
    itemLoading: boolean, //单栏loading状态
    params: [], //字段
  },
];
```

---

`params 单个控件表现`

1.<span id="selectId">name:**_select_**</span>

```javascript
  // 例子
   {
              prop: "carTypeID", // 字段名 一般为获取的id值
              label: "车辆类型",
              placeholder: "请选择",
              filterable：true, // 是否可以进行静态搜索
              isHidden：true, // 控件是否显示，默认true
              disabled: true, // 控件是否禁用，默认false
              rules: {
                required: true,  // 必填项
                message: "请选择车辆类型", // 提示信息
                trigger: "blur"
              },
              component: {
                name: "select",  // 类型
                type: "plateType", // 下拉内容 hcd-select可查看
                fields: [
                  {
                    prop: "carType", // 定义字段
                    key: "name"  // hcd-select获取的接口数据
                  }
                ]
              }
    },
```

```javascript
// 配置以上信息 可以通过

this.pageOptions.form.group[1].params.find(
  (element: any) => element.prop == "carTypeID"
).disabled = true;
```

```javascript
// 下拉框添加按钮 (配置component)

     component: {
                name: "select",  // 类型
                type: "plateType", // 下拉内容 hcd-select可查看
                rightButton: {
                  class: "hcd_button_gray",
                  text: "验证身份证",
                  methods: "validDrver", // 会由onButtonClick事件触发
                  loading: false,
                },
     },

```

2.<span id="inputId">name:**_input_**</span>

```javascript
  // 例子
   {
              prop: "name",
              label: "真实姓名",
              placeholder: "请输入真实姓名",
              maxlength: 20,
              rules: {
                required: true,
                type: "ChineseName", // 验证规则 filterRules中可见
                message: "2-20个中文可以输入圆点",
                trigger: "blur"
              },
              component: {
                name: "input",
                type: "text" // type可以改为password、textarea 、number 等
              }
            },
  // textarea
   component: {
                name: "input",
                type: "textarea",
                autosize: {
                  minRows: 2,
                  maxRows: 4
                }
              }

```

3.<span id="checkboxId">name:**_checkbox_**</span> `使用checkbox需要在初始化formData配置如下字段agreementStatus 为 false`

```javascript
  // 例子
   {
              prop: "agreementStatus",
              label: "",
              component: {
                name: "checkbox",
                data: [
                  {
                    value: false,
                    htmlText: `同意`,
                    clickHtml: `<a style="color:#409eff">《货物委托合同》</a>`,
                    activeFun: "checkboxLabel" // 点击事件
                  }
                ]
              }
            }
```

4.<span id="span">name:**_span_**</span> (展示文字)

```javascript
  // 例子
    {
              prop: "code",
              label: "推广码",
              maxlength: 4,
              component: {
                name: "span",
                value: ""
              },
              isShow: false
            }
```

5.<span id="cascaderId">name:**_cascader_**</span>（地区选择）

```javascript
  // 例子
     {
              prop: "area",
              label: "所属地区",
              placeholder: "请选择",
              rules: {
                required: true
              },
              component: {
                name: "cascader",
                type: "area",
                showAllLevels: false, //是否仅显示全部层级（name="cascader"级联下拉使用）
                changeOnSelect: true, //是否允许选择任何一级（name="cascader"级联下拉使用）
                expandTrigger: "hover", //下拉展开方式（name="cascader"级联下拉使用）
                fields: [
                  {
                    prop: "enterpriseInfo_provinceID",
                    key: "provinceID"
                  },
                  {
                    prop: "enterpriseInfo_cityID",
                    key: "cityID"
                  },
                  {
                    prop: "enterpriseInfo_districtID",
                    key: "districtID"
                  },
                  {
                    prop: "enterpriseInfo_areaName",
                    key: "areaName"
                  }
                ]
              }
            },
```

6.<span id="select-treeId">name:**_select-tree_**</span> （树结构下拉）

```javascript
  // 例子
      {
              prop: "parentId",
              label: "归属机构",
              placeholder: "请选择归属机构",
              component: {
                name: "select-tree",
                type: "department" // 在hcd-select-tree中查看
              }
            },
```

6.<span id="uploadId">name:**_upload_**</span> （图片上传）

```javascript
  // 例子
     {
              width: "50%",
              prop: "roadTransportCertificateURL",
              label: "道路运输证",
              setFieldLabel: "车辆道路运输证照片",
              placeholder: "请上传照片",
              rules: {
                required: true,
                message: "请上传正确内容",
                trigger: "blur"
              },
              component: {
                name: "upload",
                type: "image",
                multiple: false,
                limit: 1 // 限制上传数量
              }
            },
```

7.<span id="datePickerId">name:**_datePicker_**</span> （日期 时间选择）

```javascript
  // 例子
    {
              prop: "condition_Time",
              label: "单据日期",
              component: {
                name: "datePicker",
                type: "daterange",
                fields: [
                  {
                    prop: "condition_OrderDateBegin",
                    key: "start"
                  },
                  {
                    prop: "condition_OrderDateEnd",
                    key: "end"
                  }
                ],
                option:{ //// (name == datePicker 使用)
                  start	开始时间	Function, Object, String	-	-
                  end	结束时间	Function, Object, String	-	-
                  disabled	不可选日期配置	Function	-	-
                  shortcuts	自定义快捷方式	[String, Object]	-	-
                  minuteStep	分钟的间隔	Number	-	5
                  hours	自定义可选的小时	Function	-	-
                  minutes	自定义可选的分钟	Function	-	-
                }
              }
            }
```

8.<span id="radioId">name:**_radio_**</span>

```javascript
  // 例子
    {
              prop: "enterpriseInfo_authTypeEnum", //字段名
              label: "单选", //显示的标题
              disabled: false,
              rules: {
                required: true,
                message: "必须选择一项",
                trigger: "blur",
              },
              component: {
                name: "radio", //组件名
                data: [
                  {
                    value: EnterpriseAuthTypeEnum.Shipper,
                    label: "货主",
                  },
                  {
                    value: EnterpriseAuthTypeEnum.Carrier,
                    label: "承运",
                  },
                  {
                    value: EnterpriseAuthTypeEnum.ShipperAndCarrier,
                    label: "货主和承运",
                  },
                ],
              },
            },
```

9.<span id="rightSlotId">name:**_右插槽_**</span>

```javascript
  // 例子
   component: {
                rightSlot: { //右插槽
                  prop: "name", //字段名
                  name: "select", //组件名 select/text/button
                  type: "Contact", //组件数据类型
                  defaultSelect: false, //是否默认选中
                  clearable: true, //是否有清空
                  placeholder: "请输入用户名", //描述文本
                  disabled: false,//是否禁用
                  fields: [] //获取其他相关联的字段
                  query: {
                    type: 1
                  }
                  ...
                },
              },
```

10.<span id="ellipsisId">name:**_提示信息 ellipsis_**</span>

```javascript
  // 例子
   component: {
                ellipsis: true, // 提示框信息
                ellipsisSet: {
                  style: {  // 设置样式 可不传
                    position: "absolute",
                    right: 0,
                    top: 0
                  },
                  content: "123123" // 内容
                }
              },
```

11.<span id="setspanId">name:**_新增自定义 span_**</span>

```javascript
  // 例子
   component: {
                customSpan: {
                    prop: "",  // 需要在formData设置默认值
                    name: "customSpan",
                    style: "自定义样式",
                    value："默认参数"  当设置了value，prop将不生效
                }
              },
```

12.<span id="isShowId">name:**_控件显示隐藏配置 isShow_**</span>

```javascript
  // 例子
   component: {
                isShow: false, //条件计算结果
              conditionType: "or", // [or,and]
              isShowOptions: [
                //计算条件
                {
                  filed: "mophone", //formData中查找参数
                  valueStatus: "!", //非
                  value: "13" //匹配参数值
                }
              ]
              },
```
