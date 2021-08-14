## <a id="table-of-contents">目录</a>
1. [目录文件命名规范](#types)
1. [组件命名规范](#types)
1. [函数命名规范](#references)
1. [hooks命名规范](#objects)
1. [interface命名规范](#objects)
1. [api命名规范](#objects)
1. [css命名规范](#objects)


## 项目目录：文件、组件命名规范

```dotnetcli
 src/client(旧)           <-------------- nextjs 客户端代码
  |  
  + -- blocks          <----------------- 区块
  |    |
  |    + -- user           <------------- 用户相关操作区块
  |    |    |
  |    |    + -- components     <-------- 只在当前区块中使用的组件
  |    |    |    |
  |    |    |    + -- user-form    <----- 用户通用表单
  |    |    |         |
  |    |    |         + -- index.tsx
  |    |    |         | 
  |    |    |         + -- style.scss
  |    |    |
  |    |    | -- + -- detail          <--------- 用户编辑
  |    |    |    |
  |    |    | -- + -- components     <-------- 只在当前区块中使用的组件
  |    |    |    |
  |    |    |    + -- index.tsx
  |    |    |    |    介绍：当 interface、style 很少时可在当前页书写，多时则另起文件在外部书写
  |    |    |    | 
  |    |    |    + -- style.scss
  |    |    |   
  |    |    + -- index         <---------- 用户列表
  |    |    |    |
  |    |    |    + -- index.tsx
  |    |    |    | 
  |    |    |    + -- style.scss
  |    |    |     
  |    |    + -- interface.d.ts         <----- 待定：当前区块接口定义【接口内容可能有点多，时间久了，东西越多，会混乱】
  |    |                                   
  |    + -- 404        <----------------- 404 页面
  |    |    | 
  |    |    + -- index.tsx
  |    |    | 
  |    |    + -- style.scss 
  |    | 
  |    + -- 500        <----------------- 500 页面
  |    |    | 
  |    |    + -- index.tsx
  |    |    | 
  |    |    + -- style.scss 
  |    |     
  + -- components        <--------------- 全局公共基础组件
  |    |
  |    + -- button       <--------------- 按钮组件 
  |    |    | 
  |    |    + -- index.tsx
  |    |    | 
  |    |    + -- style.scss 
  |    |   
  |    + -- layouts         <------------ 布局组件 
  |    |    | 
  |    |    + -- default 
  |    |         | 
  |    |         + -- index.tsx
  |    |         | 
  |    |         + -- style.scss 
  |    |          
  + -- hooks      <---------------------- 全局hooks
  |    |
  |    + -- use-loading.ts
  |    |
  |    + -- use-mount-state.ts
  |
  + -- locales        <------------------ 国际化资源文件
  |    |
  |    + -- zh        <------------------ 中文
  |    |    |
  |    |    + -- components
  |    |    |    |
  |    |    |    + button.ts 
  |    |    |    |
  |    |    |    + icon.ts 
  |    |    |     
  |    |    + -- blocks 
  |    |         |
  |    |         + user.ts 
  |    |
  |    + -- en        <------------------ 英文
  |    |    |
  |    |    + -- components
  |    |    |    |
  |    |    |    + button.ts 
  |    |    |    |
  |    |    |    + icon.ts 
  |    |    |     
  |    |    + -- blocks 
  |    |         |
  |    |         + user.ts 
  |    |
  |    + -- index.ts
  |    |
  |    + -- interface.d.ts
  |    
  + -- ekko        <---------------------- ekko 相关
  |    |
  |    + -- services        <------------- 调用服务端接口 
  |    |    |
  |    |    + -- user 
  |    |    |    |
  |    |    |    + -- index.ts
  |    |    |    
  |    |    + -- index.ts    <------------ 接口聚合
  |    |
  |    + -- models        <--------------- ekko 对象模型
  |    |   |
  |    |   + -- user         <------------ 用户对象模型
  |    |        |
  |    |        + -- index.ts
  |    |        |
  |    |        + -- interface.d.ts
  |    | 
  |    + -- index.ts        <------------- ekko 对象模型聚合
  |        
  + -- statics       <-------------------- 全局静态资源文件如图片, svg 等  
  |    | 
  |    + -- img        <------------------ 图片 
  |    |    |
  |    |    + -- logo.png         
  |    | 
  |    + -- svg        <------------------ svg 
  |    |    |
  |    |    + -- logo.svg         
  |
  + -- styles       <-------------------- 全局样式文件
  |    |
  |    + -- base.scss  <--------------- 基础样式
  |    |
  |    + -- antd.ts    <------------ antd库重写样式
  |    |
  |    + -- variable.scss  <--------------- 全局样式变量
  |    |
  |    + -- reset.scss    <------------ 全局重写样式  
  |    |
  + -- utils           <------------------ 公共的辅助工具等
  |    |
  |    + -- function.ts <--------------- 公用函数
  |    |
  |    + -- constant.ts    <------------ 公共常量
  |    |
  |    + -- mock.ts    <---------------- 公共mock数据
  | 
  + -- pages        <--------------------- nextjs 路由  
       | 
       + -- user        <----------------- 用户页面 
       |    |
       |    + -- index        <------------ 用户列表/主入口
       |    |    |
       |    |    + -- index.ts
       |    |
       |    + -- create        <---------- 用户新增
       |    |    |
       |    |    + -- index.ts
       |    |
       |    + -- [id]        <------------ 用户详情/编辑页面
       |         |
       |         + -- index.ts
       |        
       + -- _app.tsx        <------------- nextjs _app.tsx 文件 
       |        
       + -- _document.tsx        <-------- nextjs _document.tsx 文件 
```


## 组件命名与引用规范
- 文件夹名小写、语义化 `-` 分割, 英语单词不要用 `-` 分割
  ```javascript
  // bad
  import Checkbox from './check-box'
  import Dropdown from './drop-down'
  import AutoComplete from './autocomplete'

  // good
  import Checkbox from './checkbox' 
  import Dropdown from './dropdown'
  import AutoComplete from './auto-complete' 
  ```

- 组件名、组件文件使用大驼峰，默认导出组件名称与文件名一致
  ```javascript
  /// file1 content
  class Checkbox {
    // ...
  }
  export default Checkbox
  
  // bad
  import Checkbox from './checkBox'
  import MyCheckbox from './Checkbox'

  // good
  import Checkbox from './Checkbox'
  ```

- 组件属性名为 [组件名Props]
  ```javascript
  interface CheckboxProps {
    // ...
  }
  const Checkbox: React.FC<Props> = (props) => {
    // ...
  }
  ```

- 重写三方组件重名时、三方组件命名规则 [Source组件名]
  ```javascript
  import {Checkbox as SourceCheckbox} from 'antd'
  import {CheckboxProps as SourceCheckboxProps} from 'antd/lib/checkbox'
  interface CheckboxProps extends SourceCheckboxProps {
    // ...
  }
  const Checkbox: React.FC<CheckboxProps> = (props) => {
    return (
      <Checkbox
        {...props}
      />
    )
  }
  ```

## 函数及注释命名规范

  - 命名方法： 小驼峰式命名法
  - 命名规范： 前缀应该为动词
  - 命名建议： 常用动词约定
    
  ### 动词含义
  
  |动词|含义|
  |-|-|
  |can|判断是否可执行某个动作|
  |has|判断是否含有某个值|
  |is|判断是否为某个值|
  |get|获取某个值|
  |set|设置某个值|
  |load|加载某些数据|
  |fetch|发送请求|

  ```javascript
  function canMove () {}
  function hasAuth () {}
  function isMan () {}
  function getValue () {}
  function setValue () {}
  function loadData () {}
  function fetchData () {}
  ```


## hooks命名规范

  - 文件名 use-[hooks] 开始



## interface命名规范
  - 命名方式 [模块][类型]
  - 定义参数 Param
  - 定义记录 Record
  - 定义详情 Detail
  - 记录/详情参数不能出现非必选项
  
  ```typescript
    /** 用户列表 **/
    interface UserRecord {}
    /** 用户详情 **/
    interface UserDetail {}
    /** 用户列表搜索参数 **/
    interface UserParams {}
  ```


## css命名规范
  - 选择器小写，语义化使用 `-` 分割
  ```scss
    .app-card {}
  ```
  - 类名与组件名一致
  ```javascript
    // block file
    const Dashboard = () => {
      // ...
    }

    // scss file
    .dashboard {
      // ...
    }
  ```
  - 命名方式依block(块)+function(功能)命名
  > block就是我们的组件块、function就是我们的按钮(btn)、图标(icon)等

  ```scss
    .card {
      .card-title {
        .card-title-icon {
        }
      }
      .card-content {
        // 内部再以块的形式拆解，不要再加父块做样式前缀
        .subblock1 {
          // ...
        }
      }
    }
  ```
  1. block不能超过3级含3级，超出3级默认跟父级没有关系再依新的block命名
  1. function唯一
    
  - 全局样式
  ```scss
    .ml10 {
      margin-left: 10px;
    }
    .mt10 {
      margin-top: 10px;
    }
    .mr10 {
      margin-right: 10px;
    }
    .mb10 {
      margin-bottom: 10px;
    }
    .text-align-center {
      text-align: center;
    }
    .text-align-right {
      text-align: right;
    }
    .fl {
      float: left;
    }
    .fr {
      float: right;
    }
```
