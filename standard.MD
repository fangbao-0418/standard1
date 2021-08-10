## <a id="table-of-contents">目录</a>
1. [文件命名规范](#types)
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
    1) 定义：
        const CheckBox = () => {
          return (
            <div>内容1</div>
          )
        }
        const CheckBoxMore = () => {
            return (
                <div>内容2</div>
            )
        }
        export default ChexkBox;
        export {
            CheckBoxMore
        }
    2) 引用
        import CheckBox, { CheckBoxMore } from './check-box';
        <CheckBox />
        <CheckBoxMore />


## 函数及注释命名规范
    // 切换时间选项卡 (type:时间类型)     【动宾结构：操作动作+动作内容】
    changeTimeTab(type){}
    // 打开人员列表详细弹框
    openPersonListDetails(){}


## hooks命名规范
    const [personList, setPersonList] = useState([])
    const [personObj, setPersonObj] = useReducer((state, data) => {
        ...
        return [...state, data];
    }, {})


## interface命名规范
    // I+ 定义对象。必传值靠前，非必传值靠后; 重要内容靠前，次要内容靠后。
    //【最好每个都写注释，不管是许久之后的自己维护，还是新员工维护，都能很快的理解上手，潜在的节约了时间成本】
    interface IProps {
        id:number           // 人员id
        name?:string        // 人员名称
    }
    interface IPersonInfo {}


## css命名规范
  #### 1）公共文件命名
  <p style="white-space: pre; margin-top: 0px;">
    主要的 main.css 
    基本共用 base.css
    布局、版面 layout.css
    主题 themes.css
    专栏 columns.css
    文字 font.css
    表单 form.css
    补丁 mend.css
    打印 print.css
  </p>

  #### 2）间距
  ```
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
```


## 建议
    1)简写
        样式、{key}、map、forEach、switch等
    2)多使用ES6
        扩展运算符、解构等

