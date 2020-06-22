- `onFieldChange`


返回值

| name  | type   | default | Description                            |
| ----- | ------ | ------- | -------------------------------------- |
| field | string |         | options form 配置 group 的 prop 字段名 |
| value | any    |         | 搜索框输入的参数值                     |

```javascript

  // obj.field
  onFieldChange(obj: any) {
    switch (obj.field) {
      case "字段名":
        if (!obj.value) {

        }
        break;
      default:
    }
  }

```
---

- `onPageClick`


```javascript
  /**
   * 以下方法和参数已在 GridPage中定义 需要配置时添加
   * maxResultCount
   * skipCount
   * Search
  */
  onPageClick(obj: any) {
    this.skipCount = obj.skipCount;
    this.maxResultCount = obj.maxResultCount;
    this.Search();
  }

```
---

- `onButtonClick` (为 options 中配置的 buttonGroup、buttonGroupTop、buttonGroup)


```javascript
    onButtonClick(obj: any) {
      switch (obj.methods) {
        case "方法名":
          break;
        default:
      }
    }

```
---

- `onSelectionClick` (多选框触发事件)


```javascript
 onSelectionClick(val: any) {
       // 返回选中的table 数据
  }

```

---

- `onFieldVisibleChange` (select下拉触发事件 返回值同onFieldChange一样)


```javascript
  onFieldVisibleChange(obj: any) {
    switch (obj.field) {
      case "字段名称":
        break;
        default:
    }
  }

```
