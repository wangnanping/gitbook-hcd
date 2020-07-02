##### gridPage pageOptions

[`form(输入框)`](#form) [`buttonGroup(按钮)`](#buttonGroup) [`buttonGroupTop(按钮)`](#buttonGroupTop)
[`table(表格)`](#table) [`selectableFun(表格多选框判断是否可选)`](#selectableFun) [`title(表格标题)`](#title) [`alertMessage(展示信息)`](#alertMessage)

---

| name           | type    | default    | Description                                |
| -------------- | ------- | ---------- | ------------------------------------------ |
| form           | Object  | 详解往下看 | 页面表头的搜索条件                         |
| isSearch       | Boolean | true       | 是否显示搜索、清空按钮                     |
| buttonGroup    | Array   | 详解往下看 | 搜索条件右侧按钮（默认包含搜索、清空按钮） |
| buttonGroupTop | Array   | 详解往下看 | 页面表顶部的按钮操作                       |
| table          | Object  | 详解往下看 | 表格显示配置                               |
| title          | Object  | 详解往下看 | 表格上方标题栏                             |
| alertMessage   | Object  | 详解往下看 | 表格提示信息                               |

配置项详解

---

- <span id="form">`form 配置`</span>

| name         | type    | default  | Description                       |
| ------------ | ------- | -------- | --------------------------------- |
| ref          | string  | ''       | 表格 ref                          |
| status       | string  | ''       | 页面状态[add\save\updata\details] |
| direction    | string  | ''       | [vertical\horizontal]             |
| width        | string  | '100%'   | table 宽度                        |
| elementWidth | string  | '33.33%' | 搜索条件输入框宽度                |
| labelWidth   | string  | ''       | 搜索表单 label 宽度               |
| disabled     | boolean | false    | 搜索表单所有禁用                  |
| formData     | Object  | {}       | 搜索表单的所有数据                |
| group        | Array   | []       | 搜索表单的输入框配置              |

```javascript
 {
      ref: "queryForm", //取命必须为整个项目的唯一值， 将作为缓存页码和搜索条件唯一值
      status: "add", //页面状态 [add / save / update / details]
      direction: "horizontal",//布局方式  [vertical,horizontal]
      width:"60%", //table组件宽度 默认100%
      elementWidth: "25%", //控件宽度 不设置则默认展示三列
      labelWidth: "100px", //表单label宽度
      disabled: false,//是否全局禁用 默认为false
      formData: {}, //表单数据源
      group: [
        {
          params: [
            {
              prop: "name",
              label: "用户名",
              placeholder: "请输入用户名",
              component: {
                name: "input",
                queryKeySearch: true,  // 标记为关键字搜索， 输入参数将不去除空格（只有name为input才有这个属性），默认为false  自动去除输入空格
                type: "text"
              }
            }
          ]
        },{
          params: [
            {
              prop: "name",
              label: "用户名",
              placeholder: "请输入用户名",
              component: {
                name: "select",
                type: "AvailableEnterprise",
                loadingStatus: false,
                //  只能针对select 组件
                //  可使用 this.getElement<BaseSelectComponent>("字段名").options.loadingStatus = true; 来控制loading
                //  setCall 方法来控制什么时候关闭 开启  参考目录 hcd-select
              }
            }
          ]
        }
      ]
    }

```

- <span id="buttonGroup">`buttonGroup 配置`</span>（当下可配置为[],默认显示搜索和清空按钮，如不需要显示则去掉 buttonGroup 配置项）

```javascript
// 其中有limit权限点和pagelimit页面权限参数配置，两个参数区分
[
  {
    class: "hcd_button_default",
    text: "保存",
    methods: "save",
    limit: "",
  },
  {
    class: "hcd_button_second",
    text: "返回",
    methods: "back",
    pagelimit: "",
  },
];
```

- <span id="buttonGroupTop">`buttonGroupTop 配置`</span> （当下可配置为[],默认会显示一条下划线，如不需要显示则去掉 buttonGroupTop 配置项）

```javascript
[
  {
    style: "color:red", // 配置为文字
    type: "text",
    text: "文字",
  },
  {
    class: "hcd_button_default", // 配置为按钮
    text: "添加",
    methods: "add",
  },
];
```

- <span id="table">`table 配置`</span>

| name          | type    | default | Description                                                                      |
| ------------- | ------- | ------- | -------------------------------------------------------------------------------- |
| currentPage   | number  | 0       | 当前页码，需配置为 1                                                             |
| selectableFun | funtion |         | 处理显示多选框，对单行数据做判断是否可以勾选，返回值为 boolean 值 （下方有介绍） |
| selection     | boolean | false   | 是否有多选框                                                                     |
| tableData     | Array   | []      | 为接口返回的数组参数                                                             |
| tableLabel    | Array   | []      | 配置显示的字段                                                                   |
| buttonGroup   | Array   | []      | 为表格显示的按钮（可通过配置显示装填）                                           |

```javascript

   {
      currentPage: 1, //当前页码
      selection:true, //是否有多选框
      tableData: [],
      tableLabel: [
        { prop: "name", title: "角色名称" },
        {
          prop: "status_Text",
          title: "是否启用",
          setClass: [ //设置文本class
            {
              className: "hcd_label hcd_label_success", //class
              filed: "status", //判断字段
              value: 1 //判断值 (可以为数组[1,2]，为数组时值关系为or)
            },
            {
              className: "hcd_label hcd_label_danger",
              filed: "status",
              value: 2
            }
          ],
          getContent: [ // 替换内容
              {
                  content: "内容",
                  filed: "判断字段",
                  value: 判断值
              }
          ],
          type:"html", //html代码显示
          regHtml:"${name}嗖嗖嗖${vlaue}",//匹配生成内容 name 为字段
          type: "link",
          link: "./DetailsList?carrierOrderId=${id}", //跳转
          isShow: false //列表是否显示
        },
        { prop: "值", title: "类型设置小数点" decimalHandle:{
            type:"设置类型"
        }},
        { prop: "comment", title: "备注" },
        { prop: "creationTime", title: "创建时间" },
        {  title: "操作", operation: true, fixed: "right",minWidth: "140" } // fixed固定左侧还是右侧  operation为按钮显示栏
      ],
      buttonGroup: [
        {
          class: "hcd_button_default",
          icon: "iconfont iconsetting",
          title: "修改",
          size: "mini",
          methods: "query",
          limit:"ReceiptLimit.UpdateStatusToShipperConfirm", //权限点 如果存在多个权限点['XXX','bbbb'] 数组格式
          isShow: false, //按钮是否显示
          conditionType:"and", //判断关系 [and/or] 默认and
          isShowOptions: [
            {
              dataName: "tableData", //判断数据源 [formData,tableData]
              filed: "status", //判断字段
              value: "2" //判断值
            }
          ]
        }
    ]
  }
```

- <span id="selectableFun">`selectableFun 设置`</span> （会一开始循环 table 数组的数据）

```javascript
// 设置方法
selectableFun: any = (row: any, index: any) => {
    // row为当行数据 如下为例子
  if (row.statementStatus == true) {
    return true;
  } else {
    return false;
  }
};

// table配置
 selectableFun: this.selectableFun,
```

- <span id="title">`title 设置`</span>

```javascript
  {
  title: {
    titleName: "结算信息",
  },
};
```

- <span id="alertMessage">`alertMessage 设置`</span>

```javascript
  {
 alertMessage: {
      title: "",
      type: "info", // [success/warning/info/error]
      description: "", // 辅助文字 显示在title下方
      style: "margin-top:40px;padding:20px;",
    },
};
```
