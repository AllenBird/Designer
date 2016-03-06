# 图纸设计

打包数据格式文档

## zip压缩包概要
```
  menu.json  // 树形结构，描述了ZIP包中的所有文件基础信息；详见[菜单数据]
  |-- (测试工程 id) // 测试工程文件夹
       |-- detail.json // 描述`测试工程`的详细信息，不过测试工程作为一个root节点，其实没有有价值的描述
       |-- (测试文件1 id)  // 测试文件1文件夹
            |-- detail.json // 描述`测试文件1`的详细信息；详见[设计图详情]
            |-- (测试文件1-1 id)
                |-- detail.json // 详见`设计图详情`
       |-- (测试文件2 id)
            |-- detail.json
            |-- (测试文件2-1 id)
                |-- detail.json
            |-- (测试文件2-2 id)
                |-- detail.json
                |-- (测试文件2-2-1 id)
                     |-- detail.json
                     |-- (测试文件2-2-1-1 id)
                         |-- detail.json
  |-- img // 文件夹
       |-- *.png
       |-- *.png
       |-- *.png
       |-- *.png
       |-- *.png
       |-- *.png

```
###<a name="menu"/>菜单数据

#### 修改记录

```
小鸟哥   2016-3-6   初稿
```

#### 文件说明
  
  - 数据实例

  ```json
  [
    {
      "id": "56dc3d1b975aa89c2a62e9fa",
      "text": "测试工程",
      "children": [
        {
          "id": "56dc3e45975aa89c2a62e9fd",
          "text": "测试文件1",
          "children": [
            {
              "id": "56dc3e8c975aa89c2a62ea00",
              "text": "测试文件1-1",
              "children": false
            }
          ]
        },
        {
          "id": "56dc3e45975aa89c2a62e9fe",
          "text": "测试文件2",
          "children": [
            {
              "id": "56dc3e8c975aa89c2a62ea01",
              "text": "测试文件2-1",
              "children": [
                {
                  "id": "56dc3eff975aa89c2a62ea03",
                  "text": "测试文件2-1-1",
                  "children": false
                }
              ]
            },
            {
              "id": "56dc3ee8975aa89c2a62ea02",
              "text": "测试文件2-2",
              "children": false
            }
          ]
        }
      ]
    },
    {
      "id": "56dc3ee8975aa89c2a62ea07",
      "text": "img",
      "children": [
        {
          "id": "56dc3ee8975aa8928e1321",
          "text": "空调.png",
          "children": false
        },
        {
          "id": "56dc3ee8975aa8928e1322",
          "text": "1F.png",
          "children": false
        },
        {
          "id": "56dc3ee8975aa8928e1323",
          "text": "2F.png",
          "children": false
        },
        {
          "id": "56dc3ee8975aa8928e1324",
          "text": "3F.png",
          "children": false
        }
      ]
    }
  ]
  ```

  - 数据说明

  参数名 |  说明 | 类型 | 备注
  -------|-------|------|-----
  id | 唯一标示符/文件路径 | 字符串 |
  text | 名称 | 字符串 |
  children | 子文件夹 | 数组 |

### 设计图详情

#### 修改记录

```
小鸟哥   2016-3-6   初稿
```

#### 文件说明
  
  - 数据实例

  ```json
    {
      "id": "56dc3eff975aa89c2a62ea03",
      "img": "1F.png",
      "remark": null,
      "name": "测试文件2-1-1",
      "type": "1024x768",
      "createAt": "2016-02-16T08:43:11.109Z",
      "children": false,
      "list": [
        {
          "name": "空调系统",
          "children": [
            {
              "name": "空调控制1",
              "children": false,
              "left": 63,
              "top": 94,
              "width": 82,
              "height": 73.4,
              "img":"air.png",
              "type": "AirConditioner",
              "object" : {
                "Onoff_Group_Address" : 255,
                "OnOff_Status_Group_Address" : 255,
                "Temperature_Base_Point_Group_Address" : 255,
                "Temperature_Setting_Group_Address" : 255,
                "Environment_Temperature_Group_Address" : 255,
                "Mode_Setting_Group_Address" : 255,
                "Mode_Status_Group_Address" : 255,
                "Wind_Speed_Setting_Group_Address" : 255,
                "Wind_Speed_Status_Group_Address" : 255,
                ...
              }
            },
            {
              "name": "空调控制2",
              "children": false,
              "left": 293,
              "top": 121,
              "width": 82,
              "height": 73.4,
              "img":"air.png",
              "type": "AirConditioner",
              "object" : {
                "Onoff_Group_Address" : 255,
                "OnOff_Status_Group_Address" : 255,
                "Temperature_Base_Point_Group_Address" : 255,
                "Temperature_Setting_Group_Address" : 255,
                "Environment_Temperature_Group_Address" : 255,
                "Mode_Setting_Group_Address" : 255,
                "Mode_Status_Group_Address" : 255,
                "Wind_Speed_Setting_Group_Address" : 255,
                "Wind_Speed_Status_Group_Address" : 255,
                ...
              }
            }
          ]
        },
        {
          "name": "地暖系统",
          "children": [
            {
              "name": "地暖1",
              "children": false,
              "left": 534,
              "top": 241,
              "width": 46,
              "height": 68.4,
              "img":"heat.png",
              "type": "heat",
              "object": {
                "PressDown_Group_Address" : 255,
                "PressUp_Group_Address" : 255,
                "ShortPressed_Group_Address" : 255,
                "LongPressed_Group_Address" : 255,
                "ButtonStatus_Group_Address" : 255,
                ...
              }
            }
          ]
        }
      ]
    }
  ```

  - 数据说明

  参数名 |  说明 | 类型 | 备注
  -------|-------|------|-----
  name | 对象名称 | 字符串 |
  img | 背景图路径 | 字符串 |
  remark | 备注说明 | 字符串 |
  type | 设备类型/分辨率 | 字符串 |
  createAt | 创建时间 | Date |
  list | 组件列表 | 数组 |
  left | 已左上角为原点，离左边轴的距离 | 浮点型 |
  top | 已左上角为原点，离上边轴的距离 | 浮点型 |
  width | 图片的宽 | 浮点型 |
  height | 图片的高 | 浮点型 |
  type | list中的type说明控制对象的类型 | 枚举 | 空调`AirConditioner`<br>地暖`heat`<br> ...这里还需要详细定义一下
  object | 控制对象的属性 | 对象 | 不同的type，对象属性不同
