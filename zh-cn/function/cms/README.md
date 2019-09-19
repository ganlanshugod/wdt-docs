最新更新 {docsify-updated}

## 在项目中引入内容相关组件

你可以引入整个内容组件，或是根据需要仅引入部分组件。我们先介绍如何引入完整的内容组件

##### 完整引入

在 main.js 中写入以下内容：

```
import Vue from 'vue'
import contentPlugin from '@wdt/wdt-element-ui-ueditor-content'

Vue.use(contentPlugin)
```

##### 按需引入

你可以只引入需要的组件，以达到减小项目体积的目的。比如 ContentPageDialog 组件，只需要在需要的地方写入如下内容：

```
import Vue from 'vue'
import contentPlugin from '@wdt/wdt-element-ui-ueditor-content'
Vue.use(contentPlugin.ContentPageDialog)
```

## 内容列表组件 - ContentManage

包含内容列表全部增删改查功能的列表组件

##### 先看效果

![logo](../../../_media/contentPageList.png)

##### 组件demo

```
<ContentManage
  fun-column-min-width="330px"
  show-tab-selection
  :tab-sel-list="['5d76177928b6e9667b53503c', '5d527cad32ef473f50129c2e']"
  @table-selection-change="selChange"
>
  <!-- 搜索栏左侧按钮插槽 -->
  <template #fun-button>
    <el-button>添加</el-button>
  </template>
  <!-- 列表行右侧自定义操作按钮插槽 -->
  <template #operatorbtn="{ row }">
    <el-button type="primary" size="mini" @click="click(row)">操作1</el-button>
    <el-button type="primary" size="mini" @click="click(row)">操作2</el-button>
  </template>
</>
```

##### 组件的属性列表

|          属性          |    类型     |  默认值 |            说明              |
| ---------------------- | ---------- | ------- | ----------------------------|
|   showTabSelection     |   Boolean  |   false |    是否显示表格左侧复选框     |
|   funColumnMinWidth    |   String   |   330px |  表格右侧操作列最小宽度，方便自定义操作按钮时进行自定义宽度 |
|    tabSelList          |   Array    |   []    |  默认选中内容行_id列表        |

##### 组件的事件列表

| 事件 | 触发条件 | 参数内容 |
| ---- | ---- | ------ |
|  table-selection-change    |   选中或取消选中行时触发事件   |  选中行对象列表,参考`附录1 `  |

##### 附录1：选中行对象示例(只作参考，实际对象属性根据栏目配置字段而定)

```
{
content: "<p>111</p>",
cover_img: ["5d7617b828b6e9667b535043"],
create_by: "5cbec36de944b2236ce406c9",
create_date: 1568020345985,
del_flag: false,
hot_flag: "0",
lat: "36.139839",
lng: "120.406881",
namespace: "vtsc",
recommend_flag: "1",
show_map: "0",
sort: 9999,
status: "1",
title: "附件测试数据",
type_code: "10",
update_by: "5cbec36de944b2236ce406c9",
update_date: 1568717624416,
video: ["5d76176728b6e9667b535036", "5d76177028b6e9667b535039"],
zoom: 1,
_id: "5d76177928b6e9667b53503c"
}
```

##### 插槽

| 事件 | 触发条件 | 参数内容 |
| ---- | ---- | ------ |
|  fun-button    |   搜索栏左侧自定义操作按钮   | 无 |
|  operatorbtn   |   列表行右侧自定义操作按钮   |    行对象,参考`附录1 `    |
