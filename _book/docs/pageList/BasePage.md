##### 所有页面组件如（DialogGridPage、FormPage、GridPage......等）均继承 BasePage

<br>

1.根据名称获取组件

---

```javascript
import { Form } from "element-ui";

this.getElement < Form > "ref名称";
```

根据公用子组件获取

```javascript
import BaseSelectComponent from "@/components/BaseComponent/hcd-select/hcd-select.vue";

this.getElement < BaseSelectComponent > "字段名称";
// 当前为如formPage页面组件的prop (查看可到formPage组件)
```

<br>
2.toData 方法 格式化提交formData; c 类型， data 数据， separator 分割符

---

方式：

```javascript
/**
 * SaveContactUnitInput 类
 * this.pageOptions.form.formData 为页面组件formPage 配置项
 */
this.toData(SaveContactUnitInput, this.pageOptions.form.formData);

// 会根据配置项 转化为以下数据格式
{
    xxx:"xxx"
    ......
}
```

<br>
3.toDataList 方法

---

```javascript
/**
 * BatchContactPersonInput 类
 * this.pageOptions.table.tableData 为页面组件GridPage 配置项
 */
this.toDataList(BatchContactPersonInput, this.pageOptions.table.tableData);

// 会根据配置项 转化为以下数据格式
{
    xxx:"xxx"
    ......
}
```

<br>
4.toDataForm 方法

---

```javascript
// res 格式
{
   detail:{
       name:"小王",
       age:24
   }
}

// 使用
this.toDataForm(res)

// 结果
{
  detail_name: "小王",
  detail_age: 24,
}

```

<br>
5.getformData 方法 (用于详情页面数据返回进行回绑定)

---

```javascript
// 如使用formPage页面组件配置
{
  prop: "detail_name";
}

// 接口返回
{
  detail: {
    name: "小王";
  }
}
```
