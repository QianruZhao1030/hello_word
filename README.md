# 自我介绍

面试官您好！我是赵倩茹，毕业于杭州电子科技大学计算机技术专业。在前端开发领域，我积累了较为丰富的工作经验。在 2021 年 7 月至 2025 年 2 月任职于北京转转精神科技有限公司。

任职期间，我的工作经历主要分为两个阶段：

**第一阶段**：主要负责订单交易方向的基础项目开发，比如购物车、订单详情等核心模块，为后续支付和业财系统的集成奠定基础。

**第二阶段**：聚焦于支付和业财方向，承担项目开发与部分技术方案设计，核心成果包括

1. **支付管理后台重构**：主导系统架构升级，提升稳定性和可维护性。
2. **金字塔项目**：作为项目 owner，全程负责设计方案、进度管理及风险把控，推动项目快速上线。

此外，我还深度参与了收银台与收款方式优化**、** OA 系统、发票系统及平台运营活动等项目，提供技术支持与方案优化。

这些经历使我在复杂业务场景下的系统设计、团队协作及项目管理能力得到全面锻炼。

最后，我擅长的技能有HTML，css，JS，Vue，React等，熟悉ts，antd，期待能将这些经验应用于贵司的项目中。

# 项目

### 重构原因

class写法导致处理逻辑分散，维护成本较大。代码逻辑容与，可读性较低。重复逻辑复用困难。

使用hooks写法，代码量大大减少，实现了逻辑复用。（减少了40%的重复代码）

同时也减少了类组件常见错误点（如this绑定问题），缺陷率显著下降。新人上手成本更低了、更优的逻辑单元测试体验（逻辑ui结偶，没有class初始化问题，）。

便于升级react18，class不完全支持并发渲染等功能，不利于性能优化。未来新功能接入也会有兼容问题。

### 选型依据antd+react+ts+umi

大企业背书、灵活性更高

**React**可以匹配后台系统模块化的需求，有丰富三方库，hooks简化状态逻辑，虚拟dom能高效处理操作

**umi**开箱即用，内置路由、构建、部署等，能快速启动项目。支持配置化开发，ts友好。

**ts**可以规范类型安全，智能提示，还可以定义接口（便于前后端协作），检查安全

**Ant Design** 提供很多高级组件，有设计规范，支持主题定制，组件更丰富。

### 金字塔

背景：之前业财的营收数据只能看见一个月之前的数据，金子塔是帮助公司高层能实时看到公司的财报、盈利等。

我在这个项目中是前端负责人的角色，整个项目的前端有3人，其中一个是新同学。

整个项目的我主要负责整体技术方案的设计和落地，技术我这边选择的是antd+react+ts+umi，下面从下面几个部分来介绍方案设计

- 首先是**逻辑和ui解偶**，设计的组件只是起到渲染作用，逻辑可以通过props传，这样的好处是逻辑清晰，复用性较强，更改样式只需改ui层。eg：弹窗）

- 然后是**数据管理**部分，这部分主要分为三个方向进行处理。

  - 状态管理：组件内部状态用state管理。跨组件共享的状态使用context

  - 数据流：父子props，子父回调或ref，超过两层用全局数据管理

  - 数据处理在函数中，避免在组件`<div>`中处理。

- **组件分层**这块，我们拆成了基础组件（基础的职责单一）和业务组件
- 同时，还**封装统一请求库**，基于公司的请求库并结合业务属性进行封装，主要是做了两件事
  - 统一处理接口域名：收拢在请求中，域名更换无需更改每个接口，数据请求格式（format等业务自定义数）
  - 统一错误处理：状态码、提示、错误信息等
- **最后是编码规范和协作沉淀**
  - 变量和函数名使用驼峰形式，尽量语义话。
  - 对复杂的逻辑处理需要添加注释。
  - 同时，和后端约定返回数据格式
  - 沉淀文档和最佳实践，eg组件使用指南、接口调用规范

这个项目中间遇到了一些问题，主要是因为团队里新人占比较高，加上前期流程不够规范，导致沟通成本激增，进度一度滞后，上线风险比较大。我这边也是及时进行了跟进。

首先是先分析问题，由于团队内新人较多，对业务也不熟悉。同时需求评审、开发、测试阶段都没有明确的标准，比如需求文档可读性较差，原型交互流程模糊，开发需要反复确认细节。还有开发没有考虑合作，接口定义不规范，联调阶段才暴露问题，导致大量返工。没有固定的同步机制，导致问题暴露不及时，影响上线。

针对这些问题，我做的第一件事就是制定了全流程标准化方案，明确每个阶段责任人和交付的内容。牵头梳理了项目流程七个关键阶段，每个阶段都制定了具体动作和验收标准，并且在团队内一起对齐。

- 需求评审阶段：通过⼀个标准的⽂档和原型图范例进⾏约束。

  落地：我找了公司优质的需求文档和原型图做范例，整理出需求文档和原型的模版。

  - 需求文档需要包含：背景、目标，产品方案等
  - 原型图需要展示清晰，标注逻辑交互，字段描述，校验规则
  - 需求评审前一天需要将文档和原型发出，给开发和测试审核。评审直接针对问题进行提问，避免无效会议。

  效果：文档质量高，减少了需求评审时间，更高效。开发过程减少疑问。

- **方案设计与排期阶段：技术方案 + 接口先行**

  落地：开发在需求评审后，输出接口文档和技术方案，组织团队评审，确保方案合理。排期拆解到任务，关键节点明确交付时间。（我做了接口返回数据的规范）

- **开发阶段：每日同步 + 风险可视化**

  通过站会的形式同步进度和风险，项目维护一个进度表格，若遇到阻塞问题会进行记录落实到人和解决时间。每周会整体进度分析，针对问题来落实解决方法，加人还是拆分任务。

  开发阶段末期需要review代码质量和可读性并进行自测。

- **联调和测试阶段**

  测试在联调前两天输出用例，需覆盖全流程。开发记录阻塞问题及责任人。

  测试阶段，进行测试并同步进度和风险，开发需要及时跟进阻塞错误，非阻塞问题排期处理。

- **上线与复盘阶段：计划到人 + 经验沉淀**

  制定上线计划表，明确每个步骤涉及分支、负责人和时间。

  上线后需要验证页面展示、数据准确性等

  上线一周内进行项目复盘，收集问题并落实解决方案。

这套流程推行后，后续项目的延期率大大减少，新人也能更快适应团队节奏。现在整个业财和支付方向都在沿用这套流程，提高了项目上线的质量。

#### **执行**

项目明确项目负责人，全程跟进各个节点的执行情况，及时解决卡点。对于做的好的部分表扬。违反流程会记录。

#### 项目难点

可编辑表格，自定义操作按钮，于是使用了editable. actionRender属性。编辑后获取表格的dataSource不是最新的。![img](https://api2.mubu.com/v3/document_image/28886397_dcbb69fc-2746-4080-fe80-342646672b12.png)

分析：

- Table文件中，列tableColumn相关计算使用了useMemo来缓存计算结果，其中的依赖项中没有actionRender。但是它的的处理也是在这个函数中，如果这个函数没有更新的话， 那actionRender中引用的state一直都会是旧值。

- 但是本身自带的onsave等都能拿到最新的state，对比发现actionRender中无 useRefFunction ，
  var actionCancelRef = useRefFunction(
  var actionRender = function actionRender

- 分析useRefFunction作用：通过 ref 将处理函数进⾏了保存，若给 actionRender 传⼊的是 ref.current ，然后在每次组件渲染时更新 ref.current 的指向，使得每次点击时都调⽤最新的 onClick。

**原因：useMemo是可编辑表格内部的东西，useMemo没有监听自定义的更新。**

- 改造：如果传入了自定义的actionRender，使用useRefFunction内部是时间处理可以访问最新的![img](https://api2.mubu.com/v3/document_image/28886397_ce4a9696-6485-41a0-c45d-1d27e21f0a64.png)
  https://github.com/ant-design/pro-components/pull/8547

#### 前端技术负责人

**全程负责设计方案、进度管理及风险把控，推动项目快速上线。**

- 技术方案
- 拆分任务，指导团队成员完成项目任务，按时交付，质量保证
- 关键节点跟进项目进度
- 和开发测试或其他部门合作，技术整合，合作顺利 无卡点。确保项目的整体顺利进行。

需求质量把控

- 代码质量：结构清晰、逻辑严谨、可维护性强的代码
- 兼容性和性能
- 安全性
- 测试和调试：确保功能正常、界面美观、交互流畅，及时修复bug和问题，保证项目质量。
- 与设计和后端的协作：密切合作，确保前端页面与设计保持一致，前后端数据交互正常，功能实现符合需

### 收银台接入支付渠道

**背景**：随着业务快速发展，收银台需要接入多种支付渠道。项目涉及 H5 收银台、转转小程序、采货侠小程序、客户端及第三方支付渠道 多个方向进行深度交互。

 **职责**：主要负责的是H5 收银台与转转小程序接入新的支付渠道（wqf和京东）

**问题**：小程序环境下，H5 无法直接调用小程序支付 API，需中转页作为桥梁。传统的编码方式接入的话，每次新接入支付渠道的接入都要写一个中转页面，开发、维护成本较高。

**解决**：所以考虑将中转页面的参数和逻辑分离。将配置参数的映射关系维护到公司的配置平台中，中转页面根据支付方式映射的参数进行跳转支付，支付成功后关闭页面实现流程闭环。实现 “修改配置即新增渠道” 的灵活扩展能力。

**问题**：多团队、多终端及三方合作的复杂支付项目会有一些协作问题。信息同步高度依赖 PM 对接，导致需求信息传递易出现理解偏差、沟通效率低。联调阶段暴露各端接口标准不统一，造成很多返工。支付逻辑复杂且涉及多端交互，问题定位耗时久。测试环境账号问题导致测试周期长。技术细节全靠口头沟通，关键流程、异常处理逻辑等未形成文档沉淀，后期维护难度大。

**解决**：主动建立跨部门、跨公司的沟通群，拉齐信息。联调测试阶段提前要求提供测试账号、环境等配置。联调时间拉齐，遇到问题需要及时跟进。同时，梳理项目交互流程，对接细节，关键技术问题，提炼最佳解决方案文档。

#### 难点

- **小程序**：

  IOS(返回到上一个小程序wx.navigateBackMiniProgram

  Android (打开另一个小程序): wx.navigateToMiniProgram

​	**问题**：安卓跳转回采货侠小程序会清栈，页面栈：【收银台，支付成功页】。点击返回按钮后，页面没有任何反应，无法返回到任何页面。采货侠提供的方案是在支付成功页增加按钮“返回首页”，但每个业务方的支付成功页都需要改造成本较大。

​	解决：因此需要腾讯微企付进行改造，腾讯微企付改造：wx.navigateToMiniProgram，noRelaunchIfPathUnchanged:true。不清栈。



业务方返回小程序跳转链接(拼好了支付参数的)需要通过小程序原生空白页进行跳转，跳转成功后，空白页回自动关闭
页面栈:【收银台，/pages/pay/pay，微企付】-->【收银台，微企付】
采货侠小程序回跳逻辑处理，在onshow通过判断来源场景和appiid来判断从微企付回跳，并关闭采货侠小程序白页，展示收银台

![image-20250602172903596](/Users/burst/Library/Application Support/typora-user-images/image-20250602172903596.png)

### sentry

- **背景**

  - 前端错误监控方案Sentry 是一个开源的实时错误追踪系统，可以帮助开发者实时监控并修复异常问题。对团队来说，线上质量和处理问题的效率很重要。无法辅助解决问题

  - 收集信息混乱（定位问题慢，没有合理的错误等级划分无法确认问题严重程度及类型）

  - 部分监控缺失（接口，http）

  - 没有处理错误的标准和规范

  - 无法辅助解决问题

- 目标

  - 成为日常辅助我们发现、解决项目问题的工具

  - 制定问题分级规则、问题处理标准

  - 解决存量问题

- **改造**

  - SDK 提供 beforeSend 钩子，在发送错误或消息事件之前调用该钩子，可用于修改事件数据以删除敏感信息。

- **主要工作**

  - 解决存量问题——负责中台和平台重要项目sentry的治理，每周跟进，把控治理进度。

    - 1、项目问题数减少到20以下

    - 2、收集问题及原因

    - 3、每周组内过项目问题（机器人提醒）

    - 4、每周记录问题状态，邮件汇报

  - 分析问题上报有效性

    - 5、存量问题（解决/有结论/无影响）

    - 6、及时关注新增问题

    - 7、分析问题类型（代码错误-优化，接口/sdk-有效信息帮助优化项目，三方浏览器——过滤，基础包，特殊场景）

    - 8、分析上报合理性

  - 优化上报信息

    - 9、优化sentry上报规则

    - 10、增加上报信息（traceid等）

- 收益

  - 能监控真实问题 （监测到低版本安卓白屏）

  - 中台&平台项目错误个数 < 20

  - 帮助解决线上问题

  - 团队形成意识，及时关注项目异常情况 （每周都会组内过sentry问题、error企微提醒）

  - 完善错误等级划分，报警更准确。

- **错误类型**

  - 代码错误：try...catch、window.onerror

  - 资源加载错误：object.onerror: dom对象的onerror事件、performance.getEntries()、Error事件捕获

  - 图片加载错误：performance.getEntries()

- **异常捕获**

  - 全局捕获

    - 通过全局的接口，将捕获代码集中写在一个地方。接口：window.addEventListener(‘error’)  ；window.addEventListener(“unhandledrejection”)；document.addEventListener(‘click’) 等

    - 框架级别全局监听。

      - 监控JavaScript运行时错误（包括语法错误）和 资源加载错误
        语法错误   window.onerror = function(message, source, lineno, colno, error) { ... } 
        资源加载错误  window.addEventListener('error', function(event) { ... }, true)

      - promise
        window.addEventListener("unhandledrejection", event => {  
        ​console.warn(`UNHANDLED PROMISE REJECTION: ${event.reason}`);});

      - 拦截方法，调用前处理（trycatch）setTimeout、setInterval、requestAnimationFrame

      - axios中使用interceptor

      - vue：Vue.config.errorHandler

      - React：ErrorBoundary。static getDerivedStateFromError() 或componentDidCatch(error, info)中可以捕获

    - 全局函数封装包裹

    - 对实例方法重写，在原有功能基础上包裹一层

  - 单点捕获

    - 业务代码包裹

    - try catch

    - 写一个函数收集异常，异常发生调用

    - 写一个函数包裹异常，发生可以捕获

### SelectField

**功能**：输入时展示下拉列表、支持选择输入高亮。

**设计方案**：

- 受控与非受控结合：可以内部输入，可以外部选择

- 在z-field的基础上改造，通过slot插入，聚焦展示，失焦/选择隐藏。

- 输入内容和下拉数据匹配部分，自动高亮，便于识别

- 下拉框最小高度、最大高度根据输入框和视窗动态计算，保证下拉面板不会溢出屏幕。提升了组件的健壮性和用户体验。

  ```javascript
  pannel = this.$refs.inputRef?.$el.querySelector('.field-select-panel')
  // 最小高度根据第一个推荐项的高度设置
  panel.style.minHeight = this.$refs.firstItem?.[0].offsetHeight
  // 最大高度（视窗高度 - 输入框底部位置 - 底部边距）
  panel.style.maxHeight = window.innerHeight - (fieldRect.bottom + 10);
  ```

​	只有在有推荐项且允许显示时才展示面板，否则隐藏，防止空面板出现

- 事件透传：input、focus、blur、clear、select 等事件，方便父组件监听和处理。

### 项目难点

- 全选，反选。
- 日期组件返回的是毫秒，默认是当前时间，造成日期筛选出错
- 由于升级umi4，内置不支持dva subscriptions，使用 hooks 解决 解决

​	由于升级umi4，内置react-router6，Umi 4 中将 `react-router@5` 升级到 `react-router@6`，所以路由相关的一些 api 存在着使用上的差异。

- props 默认为空对象，以下属性都不能直接从 props 中取出，history，children，match，location，等

**onRouteChange** 里面做用户访问页面没有权限，就会自动跳转到有权限的一个页面

**patchClientRoutes** 解决升级um i4后，路由配置文件，路由嵌套的时候，*redirect: '/account/search/platform/list',*  使用错误的问题，应该在子路由写 *redirect: '/account/search/platform/list',* 当没有写的情况下，patchClientRoutes里面做的兜底策略。

# 优化 &兼容 

### 移动端优化

**网络优化**

1. **资源压缩与合并**
   - 代码压缩(JS/CSS/HTML)
   - 图片压缩和合适的格式选择(WebP/AVIF)
   - 合理的文件合并策略
2. **缓存策略**
   - 浏览器缓存(Cache-Control)
   - Service Worker缓存
   - CDN缓存：CDN（Content Delivery Network，内容分发网络）是指通过在不同地理位置部署服务器，来更快、更可靠地向用户分发静态和动态网页内容的技术。CDN的作用是：加速网站访问速度，提高用户体验，降低服务器负载，提高内容的可用性和安全性。
3. **按需加载**
   - 路由懒加载
   - 组件动态导入
   - 图片懒加载

**渲染优化**

1. **关键渲染路径优化**
   - CSS放头部，JS放底部
   - 内联关键CSS
   - 异步加载非关键资源
2. **减少重排重绘**
   - 使用transform替代位置改变
   - 批量DOM操作
   - 合理使用will-change
3. **虚拟列表**
   - 长列表分页或虚拟滚动
   - 避免一次性渲染大量DOM

**代码层面优化**

1. **JavaScript优化**
   - 防抖节流
   - Web Worker处理密集计算
   - 避免内存泄漏
2. **框架层优化**
   - 合理的组件拆分
   - 响应式数据优化
   - 使用SSR/SSG

**构建优化**

1. **打包优化**webpack
   - Tree Shaking：移除未使用代码，见小宝体积
   - 代码分割(Code Splitting)：使用SplitChunksPlugin实现代码分割按需加载。
   - 压缩代码：TerserPlugin压缩js，css-minimizer-webpack-plugin压缩css
   - 异步加载
2. **现代化构建**
   - ESBuild/SWC加速构建
   - 并行构建
   - 增量构建

**监控与分析**

1. **性能指标监控**
   - FCP/LCP/TTI等指标 // 首次内容绘制/最大内容绘制/可交互时间
   - 错误监控
   - 用户行为分析
2. **持续优化**
   - 性能预算
   - CI/CD中的性能检测
   - A/B测试验证

### 图片的懒加载和预加载

预加载：提前加载图片，当用户需要查看时可直接从本地缓存中渲染。

```html
<link rel="preload" href="hero-image.jpg" as="image">
```

懒加载：懒加载的主要目的是作为服务器前端的优化，减少请求数或延迟请求数。

```html
<img src="thumbnail.jpg" loading="lazy" alt="Description">
```

两种技术的本质：两者的行为是相反的，一个是提前加载，一个是迟缓甚至不加载。
懒加载对服务器前端有一定的缓解压力作用，预加载则会增加服务器前端压力。

**图片优化**

1. **预处理**：压缩 + 转换为高效格式（WebP/AVIF）。
2. **加载控制**：懒加载 + 响应式设计(根据屏幕尺寸展示分辨率) + 优先级排序。
3. **基础设施**：CDN + 图片服务器（Node.js + Sharp） + 构建流程自动化（webpack引插件）。

**图片响应式**：视口宽度提供不同尺寸

```html
<img 
  srcset="small.jpg 500w, medium.jpg 1000w, large.jpg 2000w" //500w 表示图片宽度为 500px
  sizes="(max-width: 600px) 100vw, 50vw" //<600px 屏幕占满 100% 宽度，否则占 50%
  src="medium.jpg" 
  alt="Responsive landscape"
>
```



### 虚拟列表

**只渲染用户可见区域的元素**，三个关键步骤

1. **可视区域计算**：监听容器的滚动事件，结合容器高度和滚动位置，计算当前哪些数据在可视区域。

   ```javascript
   const scrollTop = this.$el.scrollTop;
   const startIndex = Math.floor(scrollTop / itemHeight);
   const endIndex = startIndex + visibleCount;
   ```

2. **动态渲染**：只渲染可视区域内的元素

3. 用一个占位元素填充整个列表高度，确保滚动条正常工作。

```javascript
<div class="virtual-list" @scroll="handleScroll">   
  <div class="placeholder" :style="{ height: totalHeight + 'px' }"></div>   
	<div class="content" :style="{ transform: `translateY(${offset}px)` }"> 
    <!-- 只渲染 visibleItems -->   
  </div> 
</div>
```

位置偏移：使用 CSS 的`transform`属性将渲染的元素 “移动” 到正确位置，避免重新计算布局：

```javascript
offset = startIndex * itemHeight; // 计算偏移量
```

**优化**：

​	缓冲区：可视区域上下额外渲染 5-10 个元素，减少滚动时的重渲染

​	DOM 复用：通过组件池复用已渲染的 DOM 节点

**库**：

- **Vue**：`vue-virtual-scroller`
- **React**：`react-window` 或 `react-virtuoso`
- **原生 JS**：`simple-virtual-list`

### 虚拟列表和分页

| **维度**       | **虚拟列表**                                                 | **分页**                                                     |
| -------------- | ------------------------------------------------------------ | ------------------------------------------------------------ |
| **数据获取**   | 一次性请求全部数据（或分段加载部分数据），存储在前端内存中。 | 切换页码请求对应页的数据，前端仅存储当前页数据。             |
| **数据更新**   | 需重新计算渲染范围，或触发整体数据刷新。                     | 需重新请求对应页，或通过前端局部刷新。                       |
| **渲染范围**   | 仅渲染可见区域内的列表项                                     | 渲染当前页所有数据对应的 DOM 节点                            |
| **性能表现**   | 内存占用低，滚动流畅，适合**超大数据量**（如百万级列表）。   | 内存占用随页数增加而上升，页码过多时切换页面可能出现延迟。   |
| **交互流畅度** | 滚动时无缝加载数据，无页面刷新或跳转，用户感知不到数据分段。 | 切换页码时需等待数据请求和页面刷新，可能出现空白或卡顿。     |
| **数据定位**   | 不支持直接定位到指定页码，需通过滚动查找数据（可结合搜索功能辅助）。 | 支持直接输入页码或点击页码快速定位数据，适合需要频繁跳转的数据场景。 |
| **开发成本**   | 需实现滚动监听、可见区域计算、数据缓存等逻辑，复杂度较**高**。 | 只需处理页码切换和数据请求，逻辑简单，框架（如 Vue/React）有成熟插件支持。 |
| **兼容性**     | 依赖滚动事件和现代浏览器 API，低版本浏览器可能存在兼容问题。 | 兼容性较好，传统网页和现代框架均适用。                       |

# 封装组件

**高内聚低耦合、可复用、可维护**的原则

1. **Props 设计**：明确核心功能和变体
2. **事件和插槽**：提供灵活交互和内容扩展
3. **样式与状态管理**：scoped CSS 避免样式污染；内部状态封装在内，外部通过props传
4. **工程化支持**：编写文档使用说明示例，测试常见场景

**如何灵活？**优先满足80%的场景，必要参数通过props。复杂场景通过插槽或者回调实现。复杂组件通过组件组合实现。

# 移动端适配

自适应：根据不同设备屏幕大小来调整尺寸

响应式：会随着实时变动自动调整

项目插件：postcss-pxtorem

**html fontsize = 屏幕宽度/10**

**px ➡️ rem**

宽度为375px的屏幕，100px高度，100px等于多少rem

html fontsize = 375/10 =37.5 ，100/37.5 =2.667 

### 实现响应式方法

- 媒体查询：设置html的fontsize，but区间改变不是实时
- js：html fontsize = 屏幕宽度/10 , `fontsize = document.documentElement.clientWidth /10`
- 淘宝库：lib-flexible，动态计算视口设置font-size。

## **响应式设计（适配不同屏幕尺寸）**

- **媒体查询**：可设置html的fontsize，区间改变不是实时

  ```css
  /* 平板 */ 针对不同屏幕尺寸应用不同的样式
  @media (max-width: 992px) {
    .container { width: 750px; }
  }
  ```

- **弹性布局（Flexbox & Grid）**

- **百分比**

- **rem/em 相对单位**：em: 子相对于父元素字体大小。rem: 相对于根元素`<html>`

- **viewport 布局**：vw：浏览器可见视口宽度的百分比；vh：浏览器可见视口高度的百分比

  响应式计算：html font-size = 视口宽度 ÷ 设计稿基准宽度 × 基准字体大小

  

  

  



# 单页面应用/多页面应用

- SPA：使用单个 HTML 完成多个[页面切换](https://so.csdn.net/so/search?q=页面切换&spm=1001.2101.3001.7020)和功能的应用。只有一个 html 文件作为入口，一开始只需加载一次 js,css 等相关资源。使用 js 完成页面的布局和渲染。路由跳转，仅刷新局部资源。

- MPA：多个独立的页面的应用，每个页面必须重复加载 js,css 等相关资源。多页应用跳转，需要整页资源刷新。

- 区别<img src="https://api2.mubu.com/v3/document_image/28886397_b117b319-0842-4728-e39a-6b993114abd4.png" alt="img" style="zoom: 33%;" />

# 安全（Xss）

1. 自己写数字键盘，原生键盘会被监控。
2. 实人认证三要素：手机号、身份证、活体检测（闪光颜色）。
3. 收银台支付做了验签，headers加了数字签名（md5(token-时间戳-解密明文-版本)），加密版本，时间戳
4. 支付密码通过md5加密传后端。后端是md5+uid 加密后存在数据库中。

### 攻击.方法XSS

- **跨站点脚本攻击XSS** ：将恶意代码注入到应用中，浏览器去默认执行。
  Vue 和 React 等框架有针对其的策略。
   React DOM 在渲染所有输入内容之前，默认会进行转义。它可以确保在你的应用中，永远不会注入那些并非自己明确编写的内容。所有的内容在渲染之前都被转换成了字符串

  输入过滤与输出转义，内容安全策略（CSP），HttpOnly Cookie

- **跨站点请求伪造 (CSRF)** ：通过伪装的表单、链接或按钮，诱导用户更变敏感数据
  防范：验证码、使用CSRF Token（防止恶意网站利用用户已登录的身份，）、检查Referer、~~使用从服务器生成的 CSRF 令牌。.NET等来框架的内置 CSRF 来防。~~

- SQL 注入：攻击操纵 数据库查询 以获得未经授权的数据库访问，以执行恶意活动，例如损坏数据库或窃取敏感数据。
  防范：前端输入字段经过正确验证和处理。防止用户在输入的字段中插入恶意代码。
  后端也需要进行验证，同时通过一些工具来检测SQL注入

- 中间人 (MitM)：利用不安全的通信通道（公共wifi等），监视更改用户-服务器的信息传输。
  安全互联网；不连公共wifi；HTTPS 和 TLS 等安全通信协议。

- 点击劫持：假的蒙层，诱骗用户点击与他们认为完全不同的内容
  X-Frame-Options标头，它可以确保你的网站不会嵌入到其他网站或 IFrame 中。

- 安全配置错误
  https://juejin.cn/post/7355798869110194195

- 依赖性利用


### 加密

**Base64编码**：基本的数据URL处理

**hash算法**：密码存储前的客户端预处理，HTTPS环境，需要服务端协同

- SHA-256（安全首选）
- MD5（已不安全，不推荐

**对称加密（AES**）：前端生成随机密钥，服务端返回公钥加密的密钥，前端用密钥加密数据。

**非对称加密（RSA）**：服务端生成公私钥对，前端获取公钥，前端使用公钥加密数据，服务端用私钥解密

**浏览器加密**：Web Crypto API

**为何前端加密后仍需要HTTPS？**
A: 前端加密无法防止中间人攻击，HTTPS提供端到端加密和身份验证。前端加密只在HTTPS失败时提供额外保护。

**密码传输时应该使用何种加密？**
A: 采用非对称加密传输对称密钥，再用对称加密保护密码。同时配合HTTPS并实现双因素认证。



# http & TCP 

### http2和http1的区别

http1 是请求和响应都是文本格式传输，且是顺序处理，每个连接只能处理一个请求和响应，虽然可以使用keep-alive来复用连接，但是不能解决队头阻塞的问题。每次请求和响应都是携带完整的HTTP头部，重复传输相同信息，如User-Agent,cookie等，浪费带宽。 

http2 数据是二进制传输，解析效率更高，单个TCP连接可以并发处理多个请求和响应，使用HPACK压缩头部，减少带宽占用。

### HTTP状态码

302:临时重定向，可能改变请求方法

303:临时重定向，强制使用get

307:临时重定向，保持请求方法不变

### HTTPS的加密原理

首先客户端发送请求到服务器，服务器给客户端颁发证书，且把自己的公钥和证书一起发送给客户端。证书是有CA私钥加密，客户端使用CA的公钥验证，验证成功后，客户端自己生成一个随机数预主密钥，然后用服务端的公钥加密后，发送给服务端，然后客户端和服务端根据预主密钥等条件生产会话秘钥。后续会话都使用会话密钥加密传输

### TCP和UDP

| 特性         | TCP                          | UDP                         |
| ------------ | ---------------------------- | --------------------------- |
| **连接性**   | 面向连接（三次握手）         | 无连接（直接发送）          |
| **可靠性**   | 可靠（确认机制、重传、排序） | 不可靠（可能丢包、乱序）    |
| **传输效率** | 低（头部开销 20 字节）       | 高（头部开销 8 字节）       |
| **传输方式** | 字节流（无边界）             | 数据报（有边界，不拆分）    |
| **拥塞控制** | 有（慢启动、拥塞避免）       | 无（可能导致网络拥塞）      |
| **应用场景** | HTTP、SMTP、FTP、数据库      | DNS、视频流、实时游戏、直播 |

# axios取消

- **CancelToken**（旧版）：兼容性好，通过 `source.cancel()` 取消。

```javascript
const CancelToken = axios.CancelToken;
const source = CancelToken.source();

// 发送请求，传入 cancelToken
axios.get('/api/data', {
  cancelToken: source.token
})
.then(response => {})
.catch(error => {
  if (axios.isCancel(error)) {
    console.log('请求已取消:', error.message);
  } else {
    console.log('请求错误:', error);
  }
});
// 取消请求（可在任何地方调用）
source.cancel('用户取消请求');
```

- **AbortController**（新版）：基于 Web API，代码更简洁，通过 `controller.abort()` 取消。

```javascript
const controller = new AbortController();
axios.get('/api/data', {
  signal: controller.signal // 关联 AbortController 的 signal
})
.then(response => {})
.catch(error => {
  if (error.name === 'AbortError') {
    console.log('请求已取消');
  } else {
    console.log('请求错误:', error);
  }
});
// 取消请求
controller.abort();
```

# JSX

实际是react框架的语法糖，是一种ui的写法。

通过Babel等工具编译成标准的JavaScript函数调用（如`React.createElement()`）。这些函数在React运行时被调用，生成**虚拟DOM对象**。React再将这些对象组织成**虚拟DOM树**，通过Diffing算法高效地更新真实DOM。

![image-20250612200141307](/Users/burst/Library/Application Support/typora-user-images/image-20250612200141307.png)

babel编译器转换：@babel/plugin-transform-react-jsx。配合@babel/preset-react预设

```javascript
// react16编译后
const element = React.createElement(
  "div",                       // 元素类型
  { className: "container" },  // 属性对象
  "Hello ",                    // 静态文本子节点
  name,                        // 动态表达式子节点
  "!"                          // 静态文本子节点
);

// react17编译后 (自动引入运行时函数)
import { jsx as _jsx } from 'react/jsx-runtime';
function App() {
  return _jsx("h1", {
    className: "title",
    children: "Hello World"
  });
}
```



# Webpack

js应用程序模块化打包工具

将各类资源（JS、CSS、图片等）转换为优化后的静态资产。其核心功能包括：

1. **模块打包**：处理 CommonJS、ES Modules 等多种模块格式。
2. **资源处理**：通过 Loader 转换非 JS 资源（如 `css-loader`、`file-loader`）。
3. **代码分割**：支持动态导入（`import()`）和 SplitChunksPlugin 实现按需加载。
4. **优化构建**：通过 Tree-shaking、压缩混淆、懒加载等提升性能。
5. **开发体验**：提供 HMR（热更新）、DevServer 等加速开发。

| 特性         | CommonJS                       | ES Modules (ESM)                       |
| ------------ | ------------------------------ | -------------------------------------- |
| **语法**     | `require()` / `module.exports` | `import` / `export`                    |
| **加载时机** | 同步（运行时加载）             | 异步（编译时静态分析）                 |
| **模块类型** | 对象（动态导出）               | 静态结构（导出引用）                   |
| **缓存机制** | 模块级缓存（首次加载后缓存）   | 基于 URL 的缓存（相同 URL 只执行一次） |
| **应用场景** | 服务器端（Node.js）            | 浏览器、Node.js（`.mjs`）              |
| **动态特性** | 支持动态加载（如条件加载）     | 静态结构，需使用 `import()`            |

## 构建流程

Webpack 构建流程从入口文件出发，递归解析模块依赖并生成依赖图，通过 Loader 转换处理各类资源（如 CSS、图片转 JS 模块），利用 Plugin 监听构建钩子扩展功能（如生成 HTML、提取 CSS），期间执行 Tree-shaking、代码分割、压缩混淆等优化，最终将优化后的模块合并为 Chunk，输出到指定目录生成静态资产（如 JS、CSS、HTML），实现从源码到可部署文件的自动化处理。

## Loader

`module.exports = { module: {  rules: [{...}] } }`

**babel-loader** :用babel来转换ES6文件到ES

**css-loader** :允许将css文件通过require的方式引入，分析css模块关系，合成一个css。

**style-loade**r:将css-loader生成内容，通过`style`挂载在head中。

**less-loader**: 处理less

**sass-loader**:处理sass.

**file-loader**：识别出的资源，移动到指定目录。

**postcss-loader**:用postcss来处理CSS

**autoprefixer-loader**:处理CSS3属性前缀，已被弃用，建议直接使用postcss.file-loader: 分发文件到output目录并返回相对路径

**url-loader**: 和file-loader类似，但是当文件小于设定的limit时可以返回一个Data Url

**html-minify-loader**: 压缩HTML

```javascript
//将.txt文本中的 [name] 占位符替换为指定名称。
// replace-loader.js
module.exports = function(source) {
  const options = this.getOptions() || {}; // 获取 Loader 配置参数
  const name = options.name || 'World';
  
  // 替换文本中的 [name] 占位符
  const result = source.replace(/\[name\]/g, name);
  
  // 返回处理后的结果
  return result;
};

// 先安装，再使用webpack.config.js
module.exports = {
  module: {
    rules: [
      {
        test: /\.txt$/,
        use: [
          {
            loader: path.resolve(__dirname, 'replace-loader.js'),
            options: {
              name: 'Webpack' // 传递给 Loader 的参数
            }
          }
        ]
      }
    ]
  }
};
```



## Plugin插件

`module.exports = {  plugins: [ htmlPlugin，vuePlugin] }`

plugin 赋予其各种灵活的功能，例如打包优化、资源管理、环境变量注入等，它们会运行在 webpack 的不同阶段(钩子/生命周期)，贯穿了 webpack 整个编译周期

- 引入包，zzui等

- **VuePlugin** 是 Vue 项目的核心构建工具，负责解析 `.vue` 文件。
- **HtmlPlugin** 是 Webpack 项目的通用工具，负责自动化 HTML 生成与资源注入。

## webpack和vite的区别

**构建速度**：

​	 webpack 需要将项目所有的资源，进行静态分析，生成分析依赖图，进行打包。冷启动时间长，热更新的时候需要重新构建依赖图，热更新也慢。

​	 vite 是基于现代浏览器对于原生ES的支持，无需预先打包。冷启动时间短，只更新修改的模块，无需重新构建，且利用浏览对于es module的缓存，使得热更新更快。

**开发和生产模式**： 

​	webpack 在开发和生产环境使用相同的打包机制； 

​	vite 开发环境使用原生es module（import，export），浏览器中支持启用 ES Modules按需编译。生产环境使用Rollup进行打包，生成优化的静态文件

**生态**： 

​	webpack 插件丰富，可以处理各种资源类型。社区活跃。 

​	vite 生态相对较新，但是发展迅速，插件是基于Rollup。

| 特性           | Webpack                      | Vite                                        |
| -------------- | ---------------------------- | ------------------------------------------- |
| **构建原理**   | 打包所有模块（即使未使用）   | 按需加载（基于浏览器原生 ES Modules）       |
| **冷启动速度** | 慢（需预处理所有模块）       | 极快（无需打包，直接启动）                  |
| **热更新**     | 需重新编译模块               | 仅更新修改部分（HMR 更高效）                |
| **生态成熟度** | 高（支持复杂场景和历史项目） | 中等（对 Vue/React 支持好，其他框架需适配） |
| **适用场景**   | 大型复杂应用、需精细控制打包 | 中小型项目、开发体验优先                    |

> [!NOTE]
>
> **vite**：开箱即用，插件化体系架构，支持多场景(spa,mpa等)。优势：生态强大，开发效率高，功能性强。但是开发生产是esbulid、rollup,比不上go/rust。可能存在bundless，esm的兼容问题
>
> **Rollup**：js模块打包工具。适合追求极致体积优化的场景。高效的 Tree-shaking、简洁的配置和专注 ES Modules 的特性。
>
> **typescript**：ts打包工具，可以做类型检查，支持多格式输出commonjs等，tsconfig.json可以进行打包配置。优势是前沿、类型安全保证和声明文件.d.ts在其他项目中使用。但是不适合复杂任务(代码分割，css处理，热更新)，只关注编译本身。

## Tree-shaking实现原理?

Tree-shaking是一种消除未使用代码的技术，

它依赖ES6模块的静态结构，分析import和export。构建的过程会分析依赖关系，识别删除未被引用的代码。

生产模式：会启用，使用TerserWebpackplugin 等工具进行代码压缩和优化。

配置：package.json 中将 sideEffects 设置为 false，模块中没有副作用才能安全删除

**Tree Shaking 失效的解决方案​​**
<img width="609" alt="image" src="https://github.com/user-attachments/assets/662f5eb0-0125-42b7-963f-0b7ae8eb7a1d" />

# Cookie,LocalStorage,sessionStorage

<img width="425" alt="image" src="https://github.com/user-attachments/assets/ec75c4b4-a0f0-4dcd-84e3-dc4122499c2a" />


| **特性**         | **Cookie**                                                   | **LocalStorage**                                             | **SessionStorage**                                           |
| ---------------- | ------------------------------------------------------------ | ------------------------------------------------------------ | ------------------------------------------------------------ |
| **数据类型**     | 字符串                                                       | 字符串                                                       | 字符串                                                       |
| **存储位置**     | 客户端（浏览器）                                             | 客户端（浏览器）                                             | 客户端（浏览器）                                             |
| **存储大小**     | 4KB 左右                                                     | 5MB+                                                         | 5MB+                                                         |
| **过期时间**     | `Expires`/`Max-Age` 设置                                     | 永久存储（需手动清除）                                       | 浏览器关闭或标签页关闭时清除                                 |
| **跨标签页共享** | 同一域名下，不同标签页共享（需刷新）                         | 同一域名下，不同标签页共享                                   | 仅当前标签页 / 窗口有效，不共享                              |
| **数据传输**     | ✅自动发                                                      | ❌仅读                                                        | ❌仅读                                                        |
| **典型用途**     | 身份验证（Session ID）、用户偏好设置                         | 长期存储用户数据（如主题设置）                               | 临时存储会话数据（如表单临时数据）                           |
| **存储方法**     | `document.cookie = "key=value; expires=..."`                 | `localStorage.setItem('key', 'value')`                       | `sessionStorage.setItem('key', 'value')`                     |
| **读取方法**     | `document.cookie.split('; ').find(row => row.startsWith('key='))` | `localStorage.getItem('key')`                                | `sessionStorage.getItem('key')`                              |
| **删除方法**     | 设置过期时间为过去时间                                       | `localStorage.removeItem('key')`                             | `sessionStorage.removeItem('key')`                           |
| **清空方法**     | 逐个删除或设置所有 Cookie 过期                               | `localStorage.clear()`                                       | `sessionStorage.clear()`                                     |
| **遍历方法**     | 手动解析 `document.cookie`                                   | `for (let i=0; i<localStorage.length; i++) { localStorage.key(i); }` | `for (let i=0; i<sessionStorage.length; i++) { sessionStorage.key(i); }` |

### **怎么限制cookie访问权限？**

**`Domain`**：允许访问该 Cookie 的域名，默认当前域名，子可访问。不能跨域

**`Path`**：允许访问该 Cookie 的路径，默认值为当前路径，子可访问。

**`Secure`**：仅限 HTTPS 连接发送 Cookie✅

**`HttpOnly`**：禁止 JavaScript 访问 Cookie，防xss。✅

**`SameSite`**：控制 Cookie 是否在跨站请求中发送。strict（同源）、Lax（get请求可发送，a/link/img）、None（允许发送）

限制 Cookie 有效期（`Expires`/`Max-Age`）

```javascript
Set-Cookie: Domain=example.com; Path=/api; Secure; HttpOnly; SameSite=Strict
```
# js如何执行异步操作
- 回调函数（Callback）： 作为参数传递，会造成回调地狱
- Promise
- async.await
- 时间监听：处理重复事件，用户操作
- Web Workers（浏览器）：是浏览器提供的​​后台脚本运行环境​​，允许在独立线程中执行 JavaScript 代码，实现真正的并发处理能力，避免阻塞主线程。例如处理大数据、复杂算法或高频计算时，使用 postMessage 通信传递结果。尤其适合与 Canvas 图像处理、数据分析等场景结合。不能访问dom。

  **底层原理： 事件循环**
# eventloop 事件循环

事件循环是 JavaScript 实现异步编程的核心机制。由于 JS 是单线程语言，它通过事件循环在​​主线程执行同步代码​​的同时，利用​​任务队列​​管理异步任务（如网络请求、定时器），实现非阻塞执行。

**​​关键组件​​**
​​调用栈（Call Stack）​​：执行同步代码（后进先出）
​​任务队列（Task Queue）​​：分为宏任务队列（MacroTask Queue）和微任务队列（MicroTask Queue）
​​事件循环（Event Loop）​​：持续检查调用栈是否为空，按规则将队列中的任务推入栈执行

**运行机制**
1. 执行同步代码（调用栈）
2. 清空所有**微任务**（如 `Promise.then`、`MutationObserver`）
3. 执行一个**宏任务**（如 `setTimeout`、`DOM事件`）
4. 重复步骤 2-3
   
**​​宏任务（MacroTask**）​​：setTimeout/setInterval，I/O 操作（如文件读取），UI 渲染（浏览器），setImmediate（Node.js）
**微任务（MicroTask**）​：Promise.then/async/await，queueMicrotask()，MutationObserver，process.nextTick（Node.js）

- node环境

  - 基于v8引擎运行在js环境

  - 比基本eventloop多：I/O、网络操作

  - 执行顺序

    - timer：setTimeout、setInterval

    - pending callback：调用上一次事件循环没在 poll 阶段立刻执行，而延迟的 I/O 回调函数

    - idle，prepare

    - poll：检索I/O，执行回调

    - check : 执⾏ setImmediate 回调

    - close callbacks : 执⾏ close 事件的 callback

# promise（。。）

Promise 是现代 Web 异步开发的重要组成部分，基本上目前所有的 Web 应用的异步开发手段都是通过 Promise 来实现的。

**概念**

所谓 Promise，就是一个容器对象，里面保存着某个未来才会结束的事件（异步事件）的结果。Promise 是一个构造函数，它有三个特点：

1.  Promise 有三个状态：pending（进行中）、fulfilled（成功）和 reject（失败），并且状态不受外部影响。
2.  状态一旦改变就无法修改，并且状态只能从 pending 到 fulfilled 或者是 pending 到 reject。
3.  Promise 一旦创建就会立即执行，不能中途取消。

**用法**

在 Promise 诞生之前，Web 应用中的异步开发主要采用的是回调函数的模式（详情可以参考 node.js 各个 API），回调函数的一大缺点就是，当我们的一个异步结果需要使用另外一个异步结果时，就会产生回调嵌套，一旦这样的嵌套多了，就会变成回调地狱，十分影响代码观感。

而 Promise 的诞生一定程度上解决了这个问题，因为 Promise 是采用链式调用的方式，并且在 Promise 返回的 Promise 对象中的 then、catch 等一系列方法都会返回一个新的 Promise 对象。

**then 方法**

当 Promise 实例创建成功后，可以执行其原型上的 then 方法。then 方法接受两个参数，分别是当前 Promise 的成功回调和失败回调，并且这两个函数会自动返回一个新的 Promise 对象。

then 方法的成功回调如果返回的是一个 Promise 对象，那么只有当这个 Promise 对象状态发生改变之后，才会执行下一个 then。

**catch 方法**

Promise 原型上还有一个 catch 方法，它会捕获在它链式之前的所有未被捕获的错误（一旦前面的错误被捕获，就不会执行）。

catch 只是捕获异常，catch 并不能终止当前 Promise 的链式调用。

同样的，catch 方法也会自动返回一个新的 Promise 对象，一旦显示返回一个 Promise，那么只有当这个 Promise 对象状态发生改变时，链式调用才会继续往下走。

**finally 方法**

在 ES8 中新加入的方法，此方法和 then、catch 不同，它不会跟踪 Promise 的状态，即不管 Promise 最终变成了什么状态，都会执行这个方法，同时 finally 不接收任何参数。

同样的，finally 并不是链式调用的终点，它也会自动返回一个新的 Promise 对象。

**Promise.all()** // 并发执行多个Promise，返回一个Promise，所有Promise都成功时返回成功结果，有一个失败则返回失败结

**Promise.allSettled()** // 并发执行多个Promise，返回一个Promise，所有Promise都成功或失败时返回成功或失败结果 

**Promise.any()** // 并发执行多个Promise，返回一个Promise，只要有一个Promise成功则返回成功结果，所有Promise都失败则返回失败结果 

**Promise.race()** // 并发执行多个Promise，返回一个Promise，只要有一个Promise成功或失败则返回成功或失败结果 

**Promise.resolve()** // 返回一个成功的Promise

**Promise.reject()** // 返回一个失败的Promise

# 浏览器渲染的线程都有哪些

- 主线程
  - 负责解析HTML、CSS、JavaScript
- 合成线程
  - 负责将页面分成多个图层，进行图层合成
- 光栅化线程
  - 负责将图层转换为位图，通常由GPU加速
- JavaScript引擎线程
  - 负责解析和执行JavaScript代码
- 事件处理线程
  - 负责处理事件循环，将事件分发给主线程或其他线程处理。
- 定时器线程
  - 负责处理定时器，如setTimeout、setInterval
- 网络请求线程
  - 负责处理网络请求，如XMLHttpRequest、fetch
- WebWorker线程 -允许在后台运行JavaScript代码，不阻塞主线程。
- serviceWorker线程
  - 用于实现离线缓存、推送通知等功能，独立于主线程运行。
- GPU线程
  - 负责处理GPU相关任务，如3D渲染、视频解码等。

# 页面渲染过程

- 浏览器输入Url

- 查找缓存：浏览器-系统-路由器

- DNS域名解析：浏览器向DNS服务器发起请求，解析Url的IP地址。DNS基于UDP

- 建立TCP链接：根据IP和端口和服务器建立TCP链接

- 发起Http请求：浏览器发起读取文件的Http请求，请求报文是第三次握手的数据

- 服务器响应请求返回结果：服务器对浏览器请求响应，发送html给浏览器

- 关闭TCP链接：四次挥手

- 浏览器渲染：浏览器解析html内容并渲染

  - 构建DOM树

  - 构建CSS树

  - 构建render树：浏览器将DOM和CSS结合

  - 布局：计算每个节点在屏幕位置

  - 绘制：遍历render树，使用UI后端层绘制每个节点
- 执行javascript
- 解析和执行javascript代码，可能会修改DOM或者CSSOM，引起重新布局和绘制
- 页面交互
- 关闭连接

# 重绘，重排

- 重绘：元素外观改变，布局没变。颜色透明度文本样式
- 重排：DOM变化影响元素几何信息，浏览器需要重新计算几何信息并放在正确位置。重新生成布局。元素内容大小等改变
- 如何避免：

  - 集中改变样式
- 减少DOM操作
  - 使用transform和opacity实现动画
- 虚拟dom
  - 使用will-change属性提示浏览器，will-change: transform
- fixed，position：absoult脱离文档流。
  - 不使用table布局
- 动画使用GPU，translate使用3d变化

# 防抖，节流

防抖：函数频繁触发，当停止触发后空闲一段时间后执行一次。
(回城被打断)
1秒内。只要有新的触发产生：从0开始计时。

```javascript
function debounce(fn, interval = 300) {
    let timeout = null;
    return function () {
        clearTimeout(timeout);
        timeout = setTimeout(() => {
            fn.apply(this, arguments);
        }, interval);
    };
}
```

节流：指定时间间隔内只会执行一次任务。
(技能冷却中)
1秒内。只要有新的触发产生：无效，除非之前的操作执行完。

```javascript
function throttle(fn, interval = 300) {
    let canRun = true;
    return function () {
        if (!canRun) return;
        canRun = false;
        setTimeout(() => {
            fn.apply(this, arguments);
            canRun = true;		//可以执行下一次的循环了
        }, interval);
    };
}
```

应用场景
防抖在连续的事件，只需触发一次回调的场景有：
搜索框搜索输入。只需用户最后一次输入完，再发送请求
手机号、邮箱验证输入检测
窗口大小resize。只需窗口调整完成后，计算窗口大小。防止重复渲染。

节流在间隔一段时间执行一次回调的场景有：
滚动加载，加载更多或滚到底部监听
搜索框，搜索联想功能

# 跨域

- 跨域是指由于浏览器同源策略的限制，阻止不同资源间进行访问。

- **同源策略**：协议+域名+端口。主要是限制了DOM访问，ajax请求，cookie和storage访问

- **突破思路**：

  1. **服务器代理**：同源页面请求同源服务器，服务器再转发至目标服务器。
  2. **浏览器允许**：通过 CORS 等机制让浏览器允许跨域请求。

- **解决方案**（避开这种限制）

  - **JSONP**：利用 `<script>` 标签的跨域特性（仅支持 GET 请求），通过在 URL 中添加 `callback` 参数指定回调函数获取数据。优点是兼容老浏览器（如 IE），但安全性差（易受 XSS 攻击），且功能受限。

  - **CORS（推荐）**：服务器通过设置响应头（如 `Access-Control-Allow-Origin: *`），允许指定域名或所有域名访问资源。支持 POST、PUT 等全类型请求，需服务器配合配置，现代浏览器兼容性良好（IE10+）。

    **关键响应头**：

    - `Access-Control-Allow-Origin`：允许的域名（如 `https://example.com` 或 `*`）。
    - `Access-Control-Allow-Methods`：允许的 HTTP 方法（如 `GET, POST, PUT`）。
    - `Access-Control-Allow-Headers`：允许的请求头（如 `Content-Type, Authorization`）。
    - `Access-Control-Allow-Credentials`：是否允许携带 Cookie（需与前端 `withCredentials` 配合）

  - **代理服务器**：在开发环境中（如 Webpack、Vite 配置 `proxy`）或生产环境部署独立代理服务，将跨域请求转发至目标服务器，隐藏跨域细节。需额外配置，可能增加服务器负载，但对前端透明。

  - **postMessage**：用于跨窗口通信（如 iframe 与父窗口）`window.postMessage()` 传递数据，需双方监听 `message` 事件，适用于特定场景（如多窗口协作）。

    ```javascript
    // 发送消息
    targetWindow.postMessage(message, targetOrigin, [transfer]);
    
    // 接收消息（监听 message 事件）
    window.addEventListener('message', (event) => {
      if (event.origin !== expectedOrigin) return; // 验证来源安全性
      
      const data = event.data; // 接收的数据
      const source = event.source; // 发送消息的窗口引用
    });
    ```

  - **WebSocket**：基于 `ws://` 或 `wss://` 协议，天然不受同源策略限制，支持全双工通信，适合实时交互场景（如聊天、实时数据推送）。

- **cdn不受限制**？

  - **静态资源（如 CSS、JS、图片）的跨域请求**在现代浏览器中是被**默认允许**的（除非服务器显式禁止）。因为它们不包含敏感数据，cookie等

- **cdn和主站共用域名**。

  - **限制场景**：cdn js访问敏感数据。浏览器对跨域js有更严格控制，防止注入攻击。主站启用 CSP（Content Security Policy），会显式指定允许加载资源的域名，其它不行

# 强缓存/协商缓存

- 在浏览器缓存机制中，强缓存和协商缓存是两个核心概念，它们能有效减少对服务器的请求，从而提升页面加载速度，减轻服务器压力。
- 强缓存（200（from disk cache 字体和大css/ from memory cache图片和脚本））

  - 从本地缓存中读取资源，根据缓存规则决定决定是否使用缓存结果。判断依据是请求头Expires（优先级高）和Cache-control<!--max-age=100后过期；no-cache：协商缓存；no-store：不用缓存；public：所有用户都能请求；private：只单个用户浏览器缓存，代理不能访问-->

  - 分类

    - 不存在结果和标识，强缓存失效。直接向服务器发请求

    - 存在结果和标识，但结果失效，使用协商缓存

    - 存在结果和标识，结果有效，使用强缓存，返回200
- 协商缓存（304）

  - 强缓存失效后，会先向服务器发送一个请求，询问服务器该资源是否有更新。浏览器携带缓存标识向服务器发送请求，服务器根据缓存标识判断是否使用缓存。

  - 响应头last-modified 请求的时候带if-modifie-since，最后一次文件修改的时间（s）
    首次请求，服务器会在响应头添加 Last-Modified。再请求if-modifie-since就是 Last-Modified。Last-Modified<if-modifie-since，304无修改。大于200更新

  - 请求头 Etag 和 if-none-match，比较资源内容是否改动（优先级高，资源的唯一标识）
    首次请求的时候，服务器会返回etag。再请求If-None-Match 就是etag的值。不相等，资源更新；相等取缓存304

  - 分类

    - 生效，返回304

    - 失效，返回200和结果

# Vue

## 组件通信

- **props + $emit**

  父组件绑定自定义事件@/v-on，子组件触发事件`this.$emit('fushijian',  ***)`

- **$refs**

  ```javascript
  <!-- 父组件 --> 
  <ChildComponent ref="child" /> 
  this.$refs.child.someMethod(); // 父组件中访问 
  ```

  父组件中子组件先绑定ref=aaa，mounted时可以this.$ref.aaa.$on('shijian', 箭头函数)，子组件触发事件this.$emit('fushijian',  数据)

- **Event Bus**

  1、安装全局事件总线`new Vue({... ,beforeCreate(){Vue.prototype.$bus = this},...})`
  2、接受数据组件，`this.$bus.on('shijian',箭头函数)`
  3、发送数据组件，`this.$bus.$emit('fushijian', 数据)`

- #### vuex

  - 2只能用3版本，3用4版本

  - why（共享）
    - 多个组件依赖于同一状态 不同组件的行为需要变更同一状态

  - 状态管理模式，核心是store

  - 存储状态时响应式

    - store中状态变化，相应组件会更新

    - 变更状态唯一方式就是mutation

  - 核心模块

    - state：定义数据

    - Getter：同计算属性，返回值会根据依赖存储
      store.getters.addcount

    - action：Action 提交的是 mutation，不是直接变更状态。一般会有异步函数

    - mutation：唯一更改store中状态方式，必须是同步函数

    - moudule：允许将单一的store拆分未多个，且保存在统一状态树中

- **非父子组件通信**

  - $attrs/$listeners

  ```html
  <!-- 父组件 -->
  <GrandChild :foo="foo" :bar="bar" @customEvent="handleEvent" />
  <!-- 中间组件 -->
  <Child v-bind="$attrs" v-on="$listeners" />
  <!-- 子组件 -->
  this.$attrs.bar; // 访问父组件传递的bar属性
  ```

  - provide/inject

    非响应模式provide变了，inject值不会变 


  ```javascript
// A.vue
export default {  provide: {    name: '浪里行舟'  }}/
/ B.vue
export default {  inject: ['name'],  mounted () {    console.log([this.name](http://this.name/));  // 浪里行舟  }}
  ```

  ​	响应 

  ```javascript
export default {  provide: {    theme: this  }}或provide() {  
this.theme = Vue.observable({color: "blue"});  
return {    theme: this.theme  };}
inject: {    theme: {      //函数式组件取值不一样      default: () => ({})    }  }
  ```

## Vue底层实现原理

- vue.js采用数据劫持+发布订阅模式

- Observe数据监听

  - 通过Object.defineProperty()监听数据变化，它内部可以定义getter和setter。

  - 数据变化，触发setter。

  - Observer通知Watcher

  <img src="https://api2.mubu.com/v3/document_image/28886397_5a3d967a-4206-42fd-c488-1d54ce5a4295.png" alt="img" style="zoom:25%;" />

- Watcher订阅者

  - Observe和Compile的桥梁

  - 实例化时往属性订阅器dep中添加自己

  - 有update()

  - 属性变动，dep.notice()通知，调用update()，触发Compile回调

- Compile指令解析器

  - 解析模版指令，将变量替换成数据渲染页面。

  - 每个指令对应的节点绑定更新函数，添加Watcher，数据变化更新视图

## Vue响应式原理

- vue2 使用Object.defineProperty 劫持对象属性，当属性发生变化时，触发对应的回调函数。但是不能监听数组的变化，需要使用重写数组的方法来监听。还有不能监听对象的添加和删除。嵌套数组和对象需要深度遍历。

  > [!NOTE]
  >
  > 数据劫持：把data中数据改成getter,setter形式，实现响应式。
  > 数据代理：把_data中的数据放到vm中一份，实际用的是Object.defineProperty
  > 数组中的项没有getter，setter
  > 重写数组：原型链方法+重新解析模版生成虚拟dom等流程触发试图更新。push,pop,shift,unshift,splice,sort,reverse

- vue3 使用Proxy 劫持对象，当对象的属性发生变化时，触发对应的回调函数。

- 关闭响应式<img src="https://api2.mubu.com/v3/document_image/28886397_914be960-9ced-4dd8-90e7-f366690cdeb0.png" alt="img" style="zoom: 33%;" />
  markRaw()标记对象为非响应式；toRaw()返回由 reactive 或 ref 创建的响应式对象的原始对象；shallowReactive 仅对对象的顶层属性创建响应式，shallowRef：仅对 .value 的赋值操作创建响应式

## Vue2和3区别

**响应式原理**

​	2：Object.defineProperty劫持对象属性，无法检测新增/删除属性，需要$set/$delete（不能配data中一级数据，即根数据对象）。

​	3：proxy代理。不需要遍历，会自动监听所有属性，有利于性能的提升。支持更多数据类型的响应式追踪（如Map/Set等）

**组合式api**

- vue2 生命周期钩子使用选项式API，将数据和函数集中起来处理（data/methods等选项组织代码）

- vue3 新增组合式API（setup(){响应式API生命周期名称前加 on} ），将同一个功能的代码集中起来处理支持更好的逻辑复用和代码组织

  ```javascript
  getCurrentInstance(); //vue3 setup(){}中访问当前组件实例
  ```


**性能优化**

- vue3 虚拟DOM算法优化（编译器生成带更新标记的虚拟DOM）

- vue3 打包体积更小（更好的tree-shaking支持）

- vue3 渲染速度提升（静态节点提升、事件缓存等）

**生命周期**
	创建前：beforeCreate -> **使用setup()**
	创建后：created -> **使用setup()新增**
	挂载前：beforeMount -> onBeforeMount
	挂载后：mounted -> onMounted （可访问dom）
	更新前：beforeUpdate -> onBeforeUpdate
	更新后：updated -> onUpdated （dom更新完成） //修改响应式数据，会触发新一轮更新导致无限循环，使用 `nextTick` 延迟更新可以解决
	**销毁前：beforeDestroy -> onBeforeUnmount** （清定时器，事件监听）
	**销毁后：destroyed -> onUnmounted**
	异常捕获：errorCaptured -> onErrorCaptured
	被激活：onActivated 被包含在<keep-alive>中的组件，会多出两个生命周期钩子函数。被激活时执行。
	切换：onDeactivated 比如从 A 组件，切换到 B 组件，A 组件消失时执行

**根节点**：2单根；3没有要求，默认会加fragement。减少内存

**全局API**

- vue2 全局API挂载Vue对象（Vue.use/Vue.component）

- vue3 改为应用实例API（createApp().use()）

**TypeScript支持**

- vue3 使用TypeScript重写，提供更好的类型推导

- vue3 组件选项支持类型声明（defineComponent）

**v-if /v-for优先级**

- 2v-for优先级高，v-if会分别运行在循环中。 若遍历数组大，真正展示的少，会有性能浪费。
- 3v-if高，一起使用报错。由于语法歧义，建议先使用computed过滤数据。

**diff**

- 2：遍历每一个虚拟节点，进行虚拟节点对比，并返回一个patch对象，用来存储两个节点不同的地方。 用patch记录的消息去更新dom。

- 3：给每一个虚拟节点添加一个patchFlags。只会比较patchFlags发生变化的节点，进行识图更新。



## vue3好处（******）

- 重写了虚拟 Dom 实现，编译模板的优化，更高效的组件初始化

- 更小的打包体积，减少了前端加载时间。

- 采用 TypeScript 重写，提供了更好的类型推断和类型提示。

- 灵活api

- 更好的响应系统：proxy


## 自定义指令

**对 DOM 进行底层操作的功能扩展**，用于封装可复用的 DOM 行为。

| **功能**                 | **Vue 2 钩子**     | **Vue 3 钩子**  |
| ------------------------ | ------------------ | --------------- |
| 元素挂载前               | `bind`             | `beforeMount`   |
| 元素插入 DOM 后          | `inserted`         | `mounted`       |
| 元素更新前               | `update`           | `beforeUpdate`  |
| 元素更新后（包括子元素） | `componentUpdated` | `updated`       |
| 元素卸载前               | -                  | `beforeUnmount` |
| 元素卸载后               | `unbind`           | `unmounted`     |

```javascript
// 全局注册 
  Vue.directive('viewScroll', {
    inserted: function(el) { //
      setTimeout(() => el.scrollIntoView(), 0) //元素滚动的可视区
    }
  })
// 使用
<Mycomponent v-viewScroll/>
```

```javascript
// 组件注册
export default {  directives: {    local: { /* ... */ }  } }
```

**适用场景？**

> - **指令**：聚焦、权限控制、动画效果等 **纯 DOM 操作**。
> - **组件**：封装 UI 逻辑、数据状态，适合 **复用 UI 片段**。

​	

## Vue生命周期

- beforeCreate

- created：data有值，未挂载，vue实例被创建

- beforeMount：可发请求，取数据

- mounted：操作dom

- beforeUpdate：vue实例data变化，触发组建重新渲染

- updated

- beforeDestory：可手动销毁

- destoryed

- 父子组件：父beforeCreated,父created,父beforeMounted,子beforeCreated,子created，子beforeMount，子mounted，父mounted，父beforeUpdated，子beforeDestory，子destoryed，父updated

## vue虚拟DOM

虚拟DOM实际上一个javaScript对象，用来表示真实DOM的数据结构。但是不会直接与浏览器交互，虚拟DOM的作用主要目的是减少直接操作真实DOM的次数，从而提高性能。

- 工作原理
  - 创建虚拟DOM：当一开始vue组件渲染的时候，Vue会创建一个虚拟DOM树，表示组件的结构个状态
  - 更新虚拟DOM：当组件状态发生变化的时候，Vue会重新生成一个新的虚拟DOM树
  - 比较差异：Vue使用一种差异算法，来比较新旧虚拟DOM树之间的差异。
  - 更新真实DOM：找到差异，计算出最小的DOM操作，并将这些操作应用到真实DOM上

## Vue diff

算法的核心目标是 最小化对真实dom的操作。

当组件下创建或更新时，会触发vue的update函数。update会先触发render生成一个虚拟dom树，然后将新旧虚拟dom交给patch函数来对比。

patch核心是是同层、深度优先对比，跨层就是不同节点。两节点相同标准就是key、tag是否一样

对比过程：

首先是对比根节点，如果相同就复用旧节点的真实dom，然后对比子节点；如果不相同，销毁旧节点和其真实dom，然后递归创建新节点并挂载。

然后是对比子节点，每个子节点数组用两个指针，分别指向头尾，然后采用双端比较不断向中间靠拢进行对比，尽量复用真实的dom，优先改属性或者移动，尽量减少创建和销毁真实dom。相同就是进入更新流程，新节点指向真实dom，不同就就找在旧虚拟dom是否存在，存在移动真实dom到合适位置，不存在创建节点。一直递归直到结束。

### **Vue2 双端Diff算法**

1. **遍历方式**：采用双端比较（头头、尾尾、头尾、尾头）
2. **节点复用**：通过4个指针交叉比较旧新子节点数组
3. **移动策略**：优先处理相同节点，最后处理新增/删除节点
4. **时间复杂度**：O(n) 但存在较多冗余比较

### **Vue3 快速Diff算法**

1. 预处理阶段

   - 前序相同节点直接复用，不相同停止
   - 后序相同节点直接复用，不相同停止

2. 处理仅有新增节点情况

3. 处理仅有写在节点情况

4. 处理其他情况（新增/卸载/移动）

   核心Diff

   - 构建key-index映射表（keyed fragments）
   - 寻找最长递增子序列（LIS）作为稳定锚点

   移动策略

   - 仅处理非稳定序列节点
   - 最小化DOM移动操作

   **时间复杂度**：O(n) + O(k)（k为最长递增子序列长度）

**关键差异对比**

| 特性                                                      | Vue2                | Vue3                   |
| --------------------------------------------------------- | ------------------- | ---------------------- |
| 算法类型                                                  | 双端比较            | 快速Diff + LIS优化     |
| key的作用                                                 | 辅助节点匹配        | 关键索引依据           |
| 移动优化                                                  | 简单位置交换        | 最小化DOM操作          |
| 静态节点处理                                              | 全量比较            | 静态提升跳过比较       |
| 动态列表性能                                              | 平均O(n)            | 接近O(1)稳定序列场景   |
| 内存占用                                                  | 较高（维护4个指针） | 较低（使用位运算标记） |
| vue2 使用双端比较算法，先比较头尾节点，然后比较剩余节点。 |                     |                        |

## computed & watch

- 监听

  - 都可实现监听

  - computed依赖值改变，计算属性也会改变

  - watch监听data变量，触发watch中的方法

- watch  

  - 对象：键监听属性，值回调函数

  - 一条数据影响多个

- computed

  - 值会被缓存，无改变会从缓存读取值

  - 必须returm结果

  - 多个数据影响一个

| **特性**     | **computed**（计算属性）                | **watch**（监听器）                                      | **methods**（方法）              |
| ------------ | --------------------------------------- | -------------------------------------------------------- | -------------------------------- |
| **调用方式** | 像属性一样访问（`this.fullName`）       | 监听特定数据变化触发回调                                 | 主动调用（`this.handleClick()`） |
| **缓存机制** | 依赖不变时自动缓存结果                  | 无缓存，每次变化都执行回调                               | 无缓存，每次调用都执行           |
| **适用场景** | 基于已有数据计算新值（如格式化、筛选）  | 数据变化后执行异步操作或复杂逻辑                         | 事件处理、需要副作用的操作       |
| **异步操作** | ❌                                       | ✅                                                        | ✅                                |
| **代码形式** | 声明式（返回计算结果）<br />get(),set() | 命令式（监听函数）<br />参数：handler()，deep，immediate | 命令式（函数体）                 |

## data为什么是函数

组件在复用的时候会创建多个实例，实际都是一个构造函数。

如果data是对象，它就是一个引用类型，改了一个会影响其它

# key作用

- key核心唯一标识同级元素，元素增删改时，key可以帮助快速定位哪些元素变化，避免全量查找。减少dom操作，提升diff效率
- 元素移动时，可以帮助保留状态值（输入框、动画进度等）
- 没key，默认会用index，可能导致错误复用（eg在列表头部插入元素时，索引变化会导致所有后续元素重新渲染）


**不能是index？**

1.若对数据进行:逆序添加、逆序删除等破坏顺序操作:会产生没有必要的真实DOM更新 ==>界面效果没问题，但效率低
2.如果结构中还包含输入类的DOM:会产生错误DOM更新 ==>界面有问题

| 特性                | React                     | Vue                        |
| ------------------- | ------------------------- | -------------------------- |
| **强制要求**        | 必须为列表项提供 `key`    | 非强制，但强烈推荐         |
| **推荐 `key` 类型** | 稳定 ID（如数据唯一标识） | 稳定 ID（如数据唯一标识）  |
| **索引作为 `key`**  | 不推荐，可能导致状态异常  | 允许但不推荐，性能较差     |
| **其他场景**        | 仅用于列表                | 还用于条件渲染、动态组件等 |

# vue-router路由


### hash & history

**hash**：url中带#，核心是hash改变时，通过**监听`haschange`事件**来触发事件更新视图，不触发页面刷新*。通过`window.location.hash`来修改。window.onhashchange监听到hash。**SEO 不友好**

**history**：使用html5 history api，核心是**监听`popstate`事件**来判断用户前进后退来更新视图，需要服务器支持。通过pushState和replaceState操作，无刷新页面刷新。可设置title。**CSRF 风险**：需防范伪造历史记录攻击。不支持IE9以下

`history.pushState(state, title, path)`

**单页面应用（SPA）路由管理器**，主要是实现页面级组件的动态加载（路由组件渲染`<router-view>`），url和视图同步，导航控制（前进后退跳转）。

**导航模式**

- **声明式导航**：使用 `<router-link to="/home">Home</router-link>`组件。
- **编程式导航**：使用 `router.push('/home')`or`router.push({ name: 'User', params: { id: 123 } });`，`router.replace`

**路由映射方式**有三种：声明式routes、嵌套路由、动态路由:id `this.$route.params.id; `

**导航守卫**：登录验证，权限控制

```
router.beforeEach((to, from, next) => {
  if (to.meta.requiresAuth && !isAuthenticated()) {
    next('/login'); // 未登录时重定向到登录页
  } else {
    next(); // 允许访问
  }
});
```

- 全局守卫：`beforeEach/beforeResolve/afterEach`
- 路由独享守卫：`beforeEnter`
- 组件内守卫：`beforeRouteEnter/beforeRouteUpdate/beforeRouteLeave`

**其他**

```javascript
{
  path: '/about',
  component: () => import('./views/About.vue') // 路由懒加载，使用动态 import
  meta: { requiresAdmin: true } // 自定义元信息
}
```

# nextTick

**DOM 更新后执行回调函数**

- why？

  - DOM更新是异步执行的，修改响应式数据时，会将任务放在更新队列中，抽空执行。因此你在修改后立即访问DOM会得到老数据。

- Vue的nextTick实现主要基于JavaScript事件循环机制，精准控制执行顺序，事件循环是唯一能实现 “异步等待” 的底层机制，通过将回调注册到任务队列中，让引擎在合适的时机自动执行。

  ### 关键实现机制

  1. **微任务优先**：加入任务队列

  - 优先使用Promise.then()（现代浏览器）（**UI 渲染之前**）
  - 回退方案：MutationObserver → setImmediate → setTimeout（**UI 渲染之后**执行）

  2. **异步更新队列**

  ```
  const callbacks = [] // 回调队列
  let pending = false // 批量处理标志
  
  function flushCallbacks() {
    pending = false
    const copies = callbacks.slice(0)
    callbacks.length = 0
    for (let i = 0; i < copies.length; i++) {
      copies[i]()
    }
  }
  ```

  1. **执行优先级**

  - 数据变化 → 触发Watcher → 将更新推入队列
  - 同一事件循环内的数据变化会被批量处理
  - DOM更新完成后执行nextTick回调

  ### 核心特点

  - **批处理优化**：同一tick内的多次nextTick调用会合并执行
  - **环境适配**：自动选择最优的微任务实现方式
  - **错误处理**：在微任务中捕获异常并通过console.error输出

  ### 使用示例

  ```
  // Promise风格
  this.$nextTick().then(() => {
    // DOM更新后执行
  })
  
  // 传统回调风格
  this.$nextTick(() => {
    // 可访问更新后的DOM
  })
  ```


# keep-alive

- 在组件切换时，对被移除的组件实例进行缓存

- 功能：1、组件缓存，保持组建状态。2、减少性能消耗，避免重复渲染造成性能问题。3、保留组件状态，eg表单内容、滚动条

- 三个属性：include，exclude，max

- 渲染机制：vue.is是将Dom抽象成VNode。keep-alive实际是缓存VNode组件在cache中。重新渲染时将VNode从cache中取出。

- 生命周期：activated：组件被激活时调用（组件缓存后不会触发created，mounted）。deactivated：组件被停用时调用

- 场景：tabs标签页；在单页应用（SPA）中缓存路由组件，防止用户返回时页面状态丢失

内存溢出：

- 未设置max，大组件缓存，动态组件滥用

清除： `$parent.$options.cache.delete(key)` ，deactivated清理定时器、websocket等

# 插槽

**默认插槽**：子组件定义插槽位置，父组件插入内容

子`<slot>默认内容（父组件未传值时显示）</slot>`

父`<MyComponent>  <p>自定义内容</p></MyComponent>`

**具名插槽**：子组件定义多个插槽位置，父组件通过名称区分

子`<slot name="header">默认标题</slot>`

父 `<template #header> <h1>自定义标题</h1></template>`

**动态插槽**

父 

```html
<template #[name]> <h1>自定义标题</h1></template>
const name = ref('header')
```

**作用域插槽**：vue实现 `子->父`通信的插槽，通过在子组件上绑定数据`<slot :item="item">` ，父组件通过 `v-slot="slotProps"`或`v-slot="{ item }"`接收数据并自定义渲染逻辑。其设计体现开闭原则——子组件提供数据不变，父组件决定显示方式灵活多变。

用处：收银台每项按钮。

子组件决定**渲染位置**，父组件决定**渲染内容**。

子

```html
<slot name="item" v-for="item in items" :item="item">
    {{ item.name }} <!-- 默认渲染方式 -->
</slot>
```

父

```html
<List>
  <template #item="{ item }">
    <li>{{ item.name }} ({{ item.age }})</li>
  </template>
</List>
```

# Fiber

### **1. 为什么需要 Fiber？**

在 React 15 及以前，协调器采用同步递归算法处理虚拟 DOM，这会导致长时间占用主线程，使浏览器无法及时响应用户交互（如滚动、点击），造成页面卡顿。Fiber 通过三大核心机制优化了这一过程：

### **2. Fiber 架构通过三大核心改进优化了这一过程：**

**任务切片** ➡️ **调度器：智能分配时间和优先级 ➡️ 增量渲染与双缓存：高效更新 DOM**

首先，Fiber 将虚拟 DOM 树拆解为 **Fiber 节点链表**，每个节点代表一个可独立执行的小任务。渲染时不再一次性递归完整个树，而是每次只处理一个节点，处理完就暂停，让出主线程，确保浏览器能及时响应用户操作。

其次，Fiber 引入了 **优先级调度系统**。它将主线程时间划分为多个 “时间片”，每个任务在一帧内有最大执行时间，超时则暂停。同时，为不同任务分配优先级（如用户交互 > 数据加载 > 低优先级更新），高优先级任务可中断低优先级任务，优先处理。这种协作式调度让渲染过程更灵活高效。

最后，Fiber 采用 **增量渲染与双缓存机制**。协调阶段分阶段构建 Fiber 树，标记需要更新的节点；提交阶段批量更新真实 DOM，减少重排和重绘次数。双缓存则通过在内存中同时维护两棵 Fiber 树（当前显示的树和正在计算的新树），计算完成后直接切换引用，实现无缝更新，且出错时可回滚到旧树。

### 3. 下一个要执行的 Fiber 任务呢

- 使用 深度优先遍历 + 链表指针：
  1. 先处理当前节点（比如 `<div>`）。
  2. 如果有子节点（如 `<div>` 里的 `<p>`），优先处理子节点。
  3. 子节点处理完，通过 `sibling` 指针找下一个兄弟节点（如 `<p>` 的兄弟 `<span>`）。
  4. 兄弟节点都处理完，通过 `return` 指针回到父节点。

- 类比：就像玩游戏时，先通关当前关卡的所有小 BOSS（子节点），再打下一个关卡（兄弟节点），打完所有关卡回主城（父节点）。

### 4. 如何中断和恢复

- Fiber 架构通过 **全局指针** 和 **链表结构** 实现任务的中断和恢复：
  1. **全局指针**：`workInProgress` 指向当前正在处理的 Fiber 节点
  2. **中断时**：保存 `workInProgress` 指针
  3. **恢复时**：从 `workInProgress` 指针指向的节点继续执行

- 怎么知道结束了？
  - `workInProgress` 指针为 `null`（表示没有待处理的工作单元）
  - 所有 Fiber 节点的副作用（如 DOM 更新）已收集到 `effectList` 中


### 5. Fiber 的工作阶段：render 阶段和 commit 阶段

- render 阶段：构建 Fiber 对象，构建链表，在链表中标记要执行的 DOM 操作 ，可中断。

- commit 阶段：根据构建好的链表进行 DOM 操作，不可中断。

# react diff

当你修改React组件的数据时，它不会直接去操作真实的DOM（因为DOM操作开销较大），而是先在内存里对比新旧“虚拟DOM”的差异，只更新需要变化的部分。

 这个对比过程有三个关键策略： 

1. **树形比较**：React只会比较同一层级的DOM节点。比如，如果你把一个节点从父节点A移到父节点B，React不会识别出这是“移动”，而是会直接删A建B。所以尽量避免跨层级移动节点。 
2. **组件比较**：对于React组件，类型相同只更新组件内部变化的部分；类型不同（比如从`<Button>`变成了`<Input>`）就直接整个替换掉。你还可以通过`shouldComponentUpdate`这个函数来手动控制组件是否需要更新。
3. **元素比较**：当处理列表元素（比如用`map`渲染多个子元素）时，React需要你给每个元素一个唯一的`key`（比如ID）。这样它就能知道这些元素是增删改？。如果不用key，React默认会按顺序比较元素，一旦列表顺序变了（比如插入一个新元素），就可能导致性能问题或显示错误。 

另外，React 16之后引入了Fiber架构，把这个对比过程变成了“可打断的”。也就是说，它不会一次性算完所有差异，而是拆分成很多小任务，这样不会阻塞浏览器渲染页面，用户体验会更好。

整个更新过程分成两个阶段：第一阶段计算差异生成 workInProgress Fiber 树（可打断render），第二阶段实际更新DOM（不可打断commit，执行生命周期钩子（如 `componentDidMount`）和副作用（如 useEffect））。 

最后，使用Diff算法时要记住：给列表元素加稳定的key（别用index），避免跨层级移动节点，合理使用`React.memo`或`shouldComponentUpdate`来减少不必要的比较，这样你的React应用会跑得更快。O (n³) 复杂度降至 O (n）



# class组件和函数组件

优先使用hooks组件，这是react推荐的主流方案。逻辑简洁，复用性强，更直观的数据管理。

但在以下情况我会考虑类组件：

1. 维护已有类组件组成的项目，避免全盘重写
2. 需要创建Error Boundaries这类必须使用类组件的特殊情况
3. 当团队对类组件更熟悉且项目时间压力大时作为过渡方案

![image-20250612191218424](/Users/burst/Library/Application Support/typora-user-images/image-20250612191218424.png)

- **class**：基于es6的class定义组件，接收props，返回react元素。它是数据和逻辑的封装。 也就是说，组件的状态和操作⽅法是封装在⼀起的。

- **函数**：主要就是返回一个值。数据和操作是隔离的。函数就是返回组件的 HTML 代码，返回结果只依赖于它的参数。不改变函数体外部数据、函数执⾏过程⾥⾯没有副作⽤。

- class缺点

  - 难拆分、难测试

  - 业务逻辑分散在各个组件中，会冗余。

  - 引入了复杂编程，render props

  - this

- 区别

  - 函数组件性能高
    class需要实例化，函数只需要执行返回结果即可

  - 函数：无状态组件（实例，state，生命周期，this），纯函数，依赖props

  - 调用方式

    - 函数：重新调用方法返回新的react元素

    - class：new一个新的实例（this是可变的），然后render返回react元素。

    - 操作中改变状态值，函数会按照顺序返回状态。class会直接获取到最新的状态

  

# 函数组件模拟生命周期

```javascript
// componentDidMount()  // componentWillUnmount() 
useEffect(() => {
    console.log('Component mounted');
    // 在这里执行挂载后的操作，类似于 componentDidMount
    return () => {
      console.log('Component will unmount');
      // 在组件即将卸载时执行清理操作
    };
  }, []); // 第二个参数是空数组，表示只在组件挂载和卸载时执行
```

```javascript
// componentDidUpdate() 可以比较前后的 props 或 state 变化
import React, { useEffect, useState } from 'react';
function MyComponent(props) {
  const [data, setData] = useState(props.data);
  useEffect(() => {
    console.log('Component updated');
    if (data !== props.data) {
      console.log('Data changed');
    }
  }, [data, props.data]);
  return (
    <div>
      <button onClick={() => setData('New Data')}>Change Data</button>
    </div>
  );
}
```

# hooks （react16.8新增）

- 好处：

  - 为函数组件赋能，让函数组件能处理状态和副作用（除了正常渲染处理数据外的事，修改dom，请求数据等）
  - 解决class组件逻辑复用困难，避免高阶组件嵌套
  - 摆脱this
  - 代码是按功能聚合，不是生命周期，可读性和可维护性较高。

- 必须在函数组件内使用，因为它依赖react上下文

- **useState()** //状态钩⼦

  - 管理 state，让函数组件具有维持状态的能力

  - state 中永远不要保存可以通过计算得到的值（url，props，cookie，loacalstorage）

  - class和函数组件的区别

    - 类组件中 setState 只能有一个，一个对象，不同的属性来标识不同状态

    - setState 可有多个，更加语义化，更加方便使用。

- **useReducer**() 复杂状态管理  ，状态转换机器

  - action：发生什么；dispatch：发送给reducer；reducer：处理state；返回一个新的state

  <img src="/Users/burst/Library/Application Support/typora-user-images/image-20250526155534509.png" alt="image-20250526155534509" style="zoom:25%;" />

  - 优势： 

    - 处理复杂状态逻辑（对象、依赖关系等，更新逻辑会分散到很多地方），会将状态和更新逻辑集中，可以和ui分离开。
    - 可读性、可和维护性。可测试性（可以直接给reducer函数各种state组合测试）

  - 注意：不能影响外部（api，dom操作等）；不能直接改state，需返回全新状态（对象可能会因为修改的是引用地址检测不到更新）。

  - ```javascript
    const counterReducer = (state, action) => {
      switch (action.type) {
        case 'increment':
          return { count: state.count + 1 };
        case 'decrement':
          return { count: state.count - 1 };
        case 'reset':
          return { count: action.payload }; // payload 是可选的额外数据
        default:
          throw new Error('未知 action');
      }
    };
    const [state, dispatch] = useReducer(counterReducer, { count: 0 });
    <button onClick={() => dispatch({ type: 'increment' })}>+1</button>
    ```

- **useContext()** //共享状态钩⼦

  - 通过context实现跨层级共享状态

    ```javascript
    //父
    const FatherContext = React.createContext('light');
    <FatherContext.Provider  value={{ currentUser, setCurrentUser }}>      
        <Toolbar />    
    </FatherContext.Provider>
    //子
    const { currentUser, setCurrentUser } = useContext(FatherContext);
    ```

- **useEffect()** //副作⽤钩⼦

  - useEffect是会在整个⻚⾯渲染完才会调⽤的代码

- **useLayoutEffect**

  - 在react完成DOM更新后⻢上同步调⽤的代码，会阻塞⻚⾯渲染。componentDidMount&componentDidUpdate

- **useRef** 保存引⽤值

  - 主要用于获取 DOM 节点、存储不影响渲染逻辑的变量，以及在多次渲染之间保持数据。
  - `ref` 只是一个普通对象，其<u>变化不会触发渲染</u>
  - 可以通过 ref.current 值访问组件或真实的 DOM 节点，重点是组件也是可以访问到的，从⽽可以对 DOM 进⾏⼀些操作

- **useImperativeHandle**

  - 自定义通过 ref 暴露给父组件的实例值

  - 让⽗组件获取⼦组件内的索引

    ```javascript
    // 父
    <SearchHistory ref={historySearch} />
    historySearch.current?.submit()
    ```

    ```javascript
    //子
    const SearchHistory = forwardRef((props, ref) => {
      useImperativeHandle(ref, () => ({
        submit: () => { /* ... */ }
      }));
      return <div>
    });
    ```

- **useCallback** 缓存函数，避免子组件不必要渲染

  - ~~函数组件转class组件的语法糖。重新渲染时，函数组件会将代码全都执行，方法会重新生成的。usecallback会缓存一个方法，重新渲染时不会重新生成。~~

  - ```javascript
    const memoizedCallback = useCallback(() => { doSomething(a, b) }, [a, b],);//依赖项发生变化时才重新创建函数
    ```

  - 使用场景：子组件使用 `React.memo` （缓存组件的渲染结果）时才有明显效果；性能瓶颈处使用

    ```javascript
    const MyComponent = React.memo(function MyComponent(props) {
      /* 使用 props 渲染 */
    });
    ```

- **useMemo** 缓存高开销的计算结果

  - `const memoizedValue = useMemo(() => computeExpensiveValue(a, b), [a, b]);//依赖项发生变化时才重新计算`
  - props可以控制子组件渲染
  - useCallback 不会执⾏第⼀个参数函数，⽽是将它返回给你，⽽ useMemo 会执⾏第⼀个函数并且将函数执⾏结果返回给你。


## hooks比class好处

| class                                                        | hooks                                                    |
| ------------------------------------------------------------ | -------------------------------------------------------- |
| `this` 指向混乱、构造函数冗余                                | 无需绑定this，无需构造函数，消除样板化代码               |
| 相关逻辑分散在不同生命周期方法中，如 `componentDidMount` 和 `componentWillUnmount` | `useEffect` 将相关逻辑放在一起                           |
| 高阶组件和 render props 导致组件嵌套过深（"嵌套地狱"）。     | 自定义 Hook 提取可复用逻辑                               |
| 复杂的类型定义（如 `this` 的类型、生命周期方法的类型）       | 与ts更好集成，自动推导类型，减少模板代码                 |
| shouldComponentUpdate和 `React.PureComponent` 只能进行浅比较 | 更细粒度的渲染控制React.memo` + `useCallback` + `useMemo |
| 依赖 `this` 和生命周期方法，测试时需要模拟组件实例           | 纯函数，容易测试                                         |
|                                                              | 学习成本小                                               |

# useState为什么不能放判断里

**核心限制原因**

- **链表结构依赖顺序**：React 通过调用顺序（链表索引）来关联状态和 Hooks。if会导致状态与变量完全错乱。
- **多次渲染的一致性**：必须保证每次渲染时 Hooks 的调用顺序完全相同。（React 在 **开发模式** 中会维护一个 `renderPhaseHooks` 数组，用于验证 Hooks 调用顺序，`renderPhaseHooks` 的长度会与预期不符，React 会抛出警告："Invalid hook call. Hooks must be called in the exact same order in every render."）
- **性能优化**：避免动态创建和销毁 Hooks 对象，提高渲染效率。

# react 组件通信

- ⽗组件向⼦组件通信：props传递数据or函数

- ⼦组件向⽗组件通信：父定义callback，通过props传递子组件，子组件将要传递的子通过callback传

- 状态提升（兄弟组件通信）：将共享状态提升到最近的共同父组件，通过 props 传递数据和回调

  ```javascript
  // 父组件 
  function Parent() {  
    const [count, setCount] = useState(0);    
    return (<div><IncrementButton onIncrement={() => setCount(count + 1)} />
  					<DisplayCount count={count} />    </div>  ); } 
  // 兄弟组件1 
  function IncrementButton({ onIncrement }) {  return <button onClick={onIncrement}>Increment</button>; } 
  // 兄弟组件2 
  function DisplayCount({ count }) {  return <p>Count: {count}</p>; }
  ```

- Context API（跨层级通信）：创建context组件ThemeContext，provide一个value，深层子组件可以通过useContext(ThemeContext)取到value

  ```javascript
  // 创建 Context
  const ThemeContext = React.createContext();
  // 提供者组件
  function App() {
    const [theme, setTheme] = useState('light');
    
    return (
      <ThemeContext.Provider value={{ theme, setTheme }}>
        <Header /> {/* 深层子组件 */}
      </ThemeContext.Provider>
    );
  }useReducer + Context（轻量级状态管理）
  // 深层子组件
  function Header() {
    const { theme } = useContext(ThemeContext);
    
    return (
      <header className={theme}>
        <h1>Welcome</h1>
      </header>
    );
  }
  ```

- EventBus：定义个全局事件总线，eventBus.emit发送 ，on接收。

  ```javascript
  // 创建事件总线 
  class EventEmitter {  
    constructor() {    this.events = {};  }    
    on(event, callback) {    this.events[event] = (this.events[event] || []).concat(callback);  }    
    emit(event, data) {    (this.events[event] || []).forEach(callback => callback(data));  } 
  } 
  const eventBus = new EventEmitter(); 
  // 发送组件 
  function Sender() {  const sendData = () => {    eventBus.emit('data', 'Hello from sender!');  };    return <button onClick={sendData}>Send</button>; } 
  // 接收组件 
  function Receiver() {  useEffect(() => {    const handler = (data) => console.log('Received:', data);    eventBus.on('data', handler);        return () => eventBus.off('data', handler); // 清理  
  }, []);    return <div>Listening for data...</div>; }
  ```

- 状态管理库（Redux/MobX/Recoil）

- useReducer + Context（轻量级状态管理）

  ```javascript
  // 创建 Context
  const CounterContext = React.createContext();
  
  // 定义 reducer
  const counterReducer = (state, action) => {
    switch (action.type) {
      case 'INCREMENT':
        return state + 1;
      default:
        return state;
    }
  };
  
  // 提供者组件
  function CounterProvider({ children }) {
    const [count, dispatch] = useReducer(counterReducer, 0);
    
    return (
      <CounterContext.Provider value={{ count, dispatch }}>
        {children}
      </CounterContext.Provider>
    );
  }
  
  // 使用组件
  function CounterDisplay() {
    const { count } = useContext(CounterContext);
    
    return <p>Count: {count}</p>;
  }
  ```

- refs（DOM 引用与组件通信，父子）

- 路由参数

- WebSocket

  ```javascript
  function ChatRoom() {
    const [messages, setMessages] = useState([]);
    useEffect(() => {
      const socket = new WebSocket('ws://example.com');
      socket.onmessage = (event) => {
        setMessages(prev => [...prev, JSON.parse(event.data)]);
      };    
      return () => socket.close();
    }, []); 
    const sendMessage = (text) => {
      socket.send(JSON.stringify({ text }));
    };  
    return (
      <div>
        {messages.map(msg => <p>{msg.text}</p>)}
        <input onKeyPress={sendMessage} />
      </div>
    );
  }
  ```

# redux

Redux 的核心是单向数据流架构：通过 Action 描述变化，Reducer 纯函数（不能异步）处理状态，接收state、action，生成新的state然后返回给store，Store 集中管理状态。

action是个处理对象，可以需要中间件来扩展异步处理等操作。

中间件 在action和reducer之间，`import { dynamicMiddleware } from 'redux-dynamic-middlewares';`



- store：

  ```javascript
  const store = createStore(reducer)  // createStore方法是redux提供的
  store.getState()：//获取reducer中返回的state数据；
  store.subscribe()：//用来注册监听state是否改变；
  store.dispatch()：//用于发送action，来修改reducer中的state数据；
  ```

- reducer：是一个函数，接收state、action，生成新的state

  ```javascript
  const initState={...}
  export default (state=initState,action)=>{
  	const newState = JSON.parse(JSON.stringfy(state)) ; // 由于reducer不能直接修改state，所以做下深拷贝
  	if(action.type === XXX){
  		.....    // 这块就是针对不同的action type，对数据进行不同的处理，处理完后，将最新处理完后的nesState返回给store
  	}
  	return newState；
  }
  
  ```

- action：js对象，有type表示执行的动作

<img src="https://i-blog.csdnimg.cn/direct/69ee4d6ca43942ccb990c9e5dc6adedf.png" alt="img" style="zoom:25%;" />

- 为什么用？

​	React是单向数据流，数据就是父通过props传递，子父就是通过传递函数的方式来传递修改值。数据较复杂就要用

- 核心

  - 单一数据源。state存在reducer里，这个reducer只存在唯一store
  - state是只读的。改state通过action，store.dispatch(action)
  - 使用reducer来进行修改。

  

- 使用场景

  - 获取其他组件的实时状态

  - 需要改变其它组件状态

  - 尽量不用

# setState()

# 生命周期()

# React版本

1. **React 15 及之前**：基于 Stack Reconciler 的同步渲染架构，存在性能瓶颈
2. **React 16 时期**：Fiber 架构重构奠定异步渲染基础，16.8 引入 Hooks 革命性改变开发范式
3. **React 18 时代**：
   1. 引入并发渲染能力（不阻塞主线程的情况处理多个状态更新）
   2. 通过自动批处理（合并所有场景的状态更新，减少无效渲染）、Transition API （智能区分紧急/非紧急更新，保证关键交互响应）等实现智能更新调度

关键升级包括：

- 渲染机制：同步→可中断异步→并发渲染
- 组件开发：Class 组件→函数组件+Hooks
- 服务端渲染：传统SSR→流式SSR+选择性水合"

 **React15**

- 使用循环递归虚拟DOM，使用js执行栈，需执行到任务完成为止。若虚拟dom树较深，会长时间占用主线程，此时无法进行其他操作，使页面卡顿。

**React16**

- 使用循环来模拟递归，diff过程是占用浏览器的空闲时间，解决页面卡顿。
- 三层模型

  - Scheduler (调度层)：调度任务的优先级，高优任务优先进入协调器

  - Reconciler (协调层)：构建 Fiber 数据结构，比对 Fiber 对象找出差异, 记录 Fiber 对象要进行的 DOM 操作。（15是找差异立刻更新。）

  - Renderer (渲染层)：负责将发生变化的部分渲染到页面上。（16可中断，15不可）


**React19**

- 创建了“React 编译器”。现在将管理这些重新渲染。React 将自动决定何时以及如何更改状态并更新 UI

- 服务器组件

  - 所有组件默认都是客户端的。只有当你使用 ‘use server’ 时，组件才是服务器组件

  - 优势：

    - SEO：服务器渲染的组件通过向网络爬虫提供更可访问的内容来增强搜索引擎优化。

    - 性能提升：服务器组件有助于更快地加载页面和改善整体性能，特别是对于内容密集型应用程序。

    - 服务器端执行：服务器组件使在服务器上执行代码变得无缝和高效，使诸如 API 调用之类的任务变得轻松。

- 动作：将让你将动作集成到 HTML 标签 中。
  原：<form onSubmit={search}>客户端上运行
  现：<form action={submitData}>在客户端或服务器端

- Web 组件： 在React 应用程序中利用现有的 Web 组件生态系统

- 文档元数据：直接在我们的 React 组件中使用 title 和 meta 标签

- 资源加载
  图像和其他文件将在用户浏览当前页面时在后台加载。这个改进应该有助于改善页面加载时间并减少等待时间。
  引入了用于资源加载的生命周期 Suspense，包括脚本、样式表和字体。这个特性使 React 能够确定内容何时准备好显示，消除了任何“未样式化”闪烁。

- React Hooks： 

  - 新的 use() 钩子：简化我们如何使用 promises、async 代码和 context
    const value = use(resource);

  - useFormState() 钩子：允许你基于表单提交的结果来更新状态。
    const [state, formAction] = useFormState(fn, initialState, permalink?);
    fn：当表单提交或按钮被按下时要调用的函数。
    initialState：你希望初始状态是什么值。它可以是任何可序列化的值。在首次调用后，此参数将被忽略。
    permalink：这是可选的。一个 URL 或页面链接，如果 fn 将在服务器上运行，则页面将重定向到 permalink。

  - useFormStatus()钩子
    const { pending, data, method, action } = useFormStatus();
    pending：如果表单处于挂起状态，则为 true，否则为 false。
    data：一个实现 FormData 接口的对象，包含父级 正在提交的数据。
    method：HTTP 方法 – GET 或 POST。默认情况下为 GET。
    action：一个函数引用。

  - useOptimistic() 钩子
    允许你在异步操作进行中显示不同的状态
    const [ optimisticMessage, addOptimisticMessage] = useOptimistic(state, updatefn)

# 避免react重复渲染的手段

- 使用React.memo() 包裹组件，缓存组件渲染结果
- 使用useMemo() 缓存复杂计算结果
- 使用useCallback() 缓存函数引用
- 使用useRef() 创建不变的引用对象
- 使用React.Fragment 包裹组件，避免额外DOM节点
- 使用React.StrictMode 包裹组件，检查潜在问题
# ES6

ES6是JavaScript的重大升级，我项目中全面使用了其核心特性：用`const/let`替代`var`提高可靠性；使用箭头函数和模板字符串简化代码；用Promise配合async/await处理异步逻辑；通过解构和扩展运算符高效操作数据。对模块化、类和现代数据结构(Map/Set)的应用也大幅提升了代码质量和开发效率。

- `let` 与 `const`

- 箭头函数

- 模板字符串： `Hello ${name}

- 解构赋值：数据提取新模式

- 函数参数：默认值

- 扩展运算符：解构性语法 [...arr1, ...arr2] {...obj, a:1}

- Class 类：面向对象语法糖

- Promise

- 模块化：import/export

- Symbol：唯一标识符

- 集合类型：Set & Map

  ``````
  set.add() ;set.has();   set.size()
  map.set(); map.has();   map.get()
  ``````

- Iterators & Generators:

  ``````javascript
  const numbers = [1, 2, 3];
  const iterator = numbers[Symbol.iterator]();
  console.log(iterator.next()); // {value: 1, done: false}
  console.log(iterator.next()); // {value: 2, done: false}
  console.log(iterator.next()); // {value: 3, done: false}
  console.log(iterator.next()); // {value: undefined, done: true}
  
  function* idGenerator() {
      let id = 1;
      while (true) {
          yield id++;
      }
  }
  
  const gen = idGenerator();
  console.log(gen.next().value); // 1
  console.log(gen.next().value); // 2
  console.log(gen.next().value); // 3
  ``````

  

# this

- 全局作用域：this是window（浏览器环境）、global（node环境）

- 函数指向window（严格模式undefined）；对象指向对象；构造函数指向新创建对象

- 箭头函数this是继承外部函数

- dom指向触发事件的元素

- call、apply 或 bind改变内部指向
  bind：返回一个新的函数，新函数的 this 指向被绑定为指定的值
  call、apply：立即调用函数，并且第一个参数是 this 的指向
  `​function.call(new,arg1, arg2, ...])`

  `fuction.bind(obj)`

  `function.apply(new, [arg1, arg2, ...])`

# bind，call，apply

```
Function.prototype.myBind = function(context, ...args) {
  const originalFunc = this

  return function(...newArgs) {
    const combinedArgs = args.concat(newArgs)
    const result = originalFunc.apply(context, combinedArgs)
    return result
  }
}
```

```
Function.prototype.myCall = function(context, ...args) {
  // 1. 处理 undefined 和 null 的上下文
  context = context || window; // 浏览器环境用 window，Node.js 需改为 globalThis
  // 2. 创建唯一键避免属性覆盖
  const fnKey = Symbol('__tempFn__');
  // 3. 将当前函数绑定到上下文
  context[fnKey] = this; // this 指向原函数
  // 4. 执行函数并保存结果
  const result = context[fnKey](...args);
  // 5. 清理临时属性
  delete context[fnKey];
  // 6. 返回执行结果
  return result;
};
```

```
Function.prototype.myApply = function(context, argsArray) {
  // 类型安全检查
  if (typeof this !== 'function') {
    throw new TypeError('调用者必须是函数');
  }
  // 处理上下文
  context = context != null ? Object(context) : window;
  // 创建唯一键
  const fnKey = Symbol('fn');
  // 绑定函数
  context[fnKey] = this;
  // 参数处理
  let result;
  if (!argsArray) {
    result = context[fnKey]();
  } else {
    if (!Array.isArray(argsArray) && !isArrayLike(argsArray)) {
      throw new TypeError('第二个参数必须为数组或类数组');
    }
    result = context[fnKey](...Array.from(argsArray));
  }
  // 清理
  delete context[fnKey];
  return result;
};
```

# new

```HTML
const newInstance = (fn, ...args) => {
  const obj = Object.create(fn.prototype) // 创建一个新对象，继承构造函数的原型
  const res = fn.apply(obj, args) // 将构造函数的this指向新创建的对象，并传入参数
  return res instanceof Object ? res : obj // 如果构造函数返回的是一个对象，则返回该对象，否则返回新创建的对象
}
```

# 原型

**原理**：函数和对象的内置机制，用于共享属性和方法。

- **`prototype`**原型：函数特有的属性，指向原型对象，用于定义共享方法。

- **`__proto__`**：对象（包括函数和原型对象）的隐式属性，指向父级原型对象，用于实现原型链查找

- ```javascript
  //是否是该对象的原生属性：
  teacher.hasOwnProperty('name')
  //判断属性是否在原型链上
  obj.hasOwnProperty(key) === false && key in obj
  ```

**原型链**：是对象查找属性的路径，通过 `__proto__` 层层向上关联，形成链式结构

- 每个对象（除null）都有 `__proto__` 属性，这个属性指向了创建该对象的构造函数的原型。没找到就沿着proto向上查找，层层向上直到Object.prototype，这样就形成了原型链。

  `隐式student.__proto__ === 显式Student.prototype` 

- **特点**：
  当访问对象属性时，如果对象内部没有这个属性，就会沿着原型链一直往上找；
  当修改原型时，与之相关的对象也会继承这一改变。

  Person.prototype.name 这种的写法是在原有的基础上把值改了。 改的是属性，也就是房间里面的东西。
  而 Person.prototype={name:’ cherry’ }是把原型改了，换了新的对象。 改了个房间。_proto_指向的空间不变

  

  ![](https://img-blog.csdnimg.cn/2020073011130453.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2J1cnN0Z2lybHM=,size_16,color_FFFFFF,t_70)



**为什么共享属性？**

- 内存优化：多个对象需要相同方法，在原型上定义就能做到共享。
- 维护：修改原型链上属性会影响所有实例，便于批量更新
- 继承的核心，实现复用扩展



~~**构造函数、原型、实例之间的关系**~~

~~每个实例对象（ object ）都有一个私有属性（称之为 `__proto__ `）指向它的构造函数的原型对象（**prototype** ）。该原型对象也有一个自己的原型对象( `__proto__ `) ，层层向上直到一个对象的原型对象为 `null`。根据定义，`null` 没有原型，并作为这个**原型链**中的最后一个环节。~~

~~每个构造函数都有一个原型对象(prototype)，原型对象都包含一个指向构造函数的指针（constructor），而实例都包含一个指向原型对象的内部指针（`__proto__`）。~~

Object.create(原型);
Object.prototype 是原型链的终端

# 继承

**JavaScript 继承是指一个对象直接使用另一对象的属性和方法**

1. **原型链**：每个对象都有一个内部属性 `[[Prototype]]`（可通过 `__proto__` 访问），指向其原型对象。当访问对象的属性时，JavaScript 会先查找对象本身，再沿原型链向上查找，直到 `Object.prototype` 或 `null`。
2. **构造函数**：通过 `new` 关键字调用的函数，用于创建对象实例，实例会继承构造函数原型（`prototype`）上的属性和方法。

| 继承方式       | 优点               | 缺点                   | 适用场景           |
| -------------- | ------------------ | ---------------------- | ------------------ |
| 原型链继承     | 实现简单           | 共享引用类型、无法传参 | 仅继承方法         |
| 构造函数继承   | 独立属性、可传参   | 无法继承原型链         | 仅继承属性         |
| 组合继承       | 同时继承属性和方法 | 调用两次父类构造函数   | 兼容性要求高的场景 |
| 寄生组合继承   | 最优方案           | 实现复杂度较高         | 性能敏感的场景     |
| ES6 Class 继承 | 语法简洁、语义清晰 | 依赖 ES6 环境          | 现代项目           |

**原型链继承**

```javascript
function Parent() {
  this.name = 'parent';
  this.colors = ['red', 'blue'];
}

Parent.prototype.say = function() {
  console.log('hello');
}

function Child() {}
Child.prototype = new Parent(); // 关键：子类的原型是父类的实例，child.__proto__ === Parent.prototype;

const child1 = new Child();
child1.colors.push('green'); // child1.colors：['red', 'blue', 'green']
const child2 = new Child(); // child2.colors：['red', 'blue', 'green'] ❗共享引用类型
```

**构造函数继承**

```javascript
function Parent(name) {
  this.name = name;
  this.colors = ['red', 'blue'];
}

Parent.prototype.sayHi = function() {
  console.log('Hi from Parent');
};

function Child(name, age) {
  Parent.call(this, name); // 关键: 在子类构造函数中调用父类构造函数，通过 call/apply 绑定父类上下文
  this.age = age;
}

const child1 = new Child('Alice', 20);
child1.colors.push('green'); //child1.colors): ['red', 'blue', 'green']
const child2 = new Child('Bob', 25); // child2.colors:['red', 'blue'] ✅独立引用类型
```

**组合继承**

```javascript
function Parent(name) {
  this.name = name;
  this.colors = ['red', 'blue'];
}

Parent.prototype.say = function() {
  console.log('hello');
}

function Child(name, age) {
  Parent.call(this, name); // 第一次调用父类构造函数
  this.age = age;
}

Child.prototype = new Parent(); // 第二次调用父类构造函数
Child.prototype.constructor = Child;
```

**寄生组合继承**

```javascript
function Parent(name) {
  this.name = name;
  this.colors = ['red', 'blue'];
}

Parent.prototype.say = function() {
  console.log('hello');
}

function Child(name, age) {
  Parent.call(this, name); // 继承属性，第一次调用父类构造函数
  this.age = age;
}

// 继承原型
Child.prototype = Object.create(Parent.prototype); // 关键：直接继承父类原型
Child.prototype.constructor = Child; // 修正 constructor

// 子类可以添加自己的方法
Child.prototype.play = function() {
  console.log('playing');
};
```

**ES6 Class 类继承（语法糖）**

```
class Parent {
  constructor(name) {
    this.name = name;
    this.colors = ['red', 'blue'];
  }
  
  say() {
    console.log('hello');
  }
}

class Child extends Parent {
  constructor(name, age) {
    super(name);           // 必须先调用super
    this.age = age;
  }
  
  play() {
    console.log('playing');
  }
}
```

**多重继承**

```javascript
const Mixin1 = { method1() {} };
const Mixin2 = { method2() {} };

class MyClass { /* ... */ }
Object.assign(MyClass.prototype, Mixin1, Mixin2);
```

# 深拷贝/浅拷贝

- 浅拷贝：拷贝对象，属性是引用类型，两个对象共享一块内存，修改一个对影响另一个.
  Object.assign(target, ...sources) 或  {...obj} 或 Array.slice()或[...arr]

- 深拷贝：会递归地复制原始对象的所有属性，生成是一个新对象

  ```javascript
  JSON.parse(JSON.stringify(obj)) 
  ```

  **边界状况**：建议用三方库lodash.cloneDeep
  1、基本数据类型：null，undefined，number，string，boolean直接返回
  2、对象，数组 需要递归拷贝
  3、循环引用，使用WeakMap 记录已处理的对象。

  ```javascript
  function deepCopy(obj, cache = new WeakMap()) {
    if (typeof obj !== 'object' || obj === null) return obj;
    
    // 处理循环引用
    if (cache.has(obj)) return cache.get(obj);
    
    const copy = Array.isArray(obj) ? [] : {};
    cache.set(obj, copy); // 缓存当前对象
    
    for (const key in obj) {
      if (obj.hasOwnProperty(key)) {
        copy[key] = deepCopy(obj[key], cache); // 递归并传递缓存
      }
    }
    
    return copy;
  }
  
  // 测试循环引用
  const a = {};
  a.b = a; // 循环引用
  const copy = deepCopy(a);
  console.log(copy.b === copy); // 输出: true（正确处理循环引用）
  ```

  4、特殊对象：日期对象（Date）return new Date(obj.getTime());正则表达式（RegExp）return new RegExp(obj);Map/Set；Function
  5、不可枚举属性，Symbol
  6、原型链

# 作用域let，const，var

- 变量与函数的访问范围

  - 全局作用域：在程序任何地方都能访问，eg：window属性

  - 函数作用域：固定代码片段使用

- 创建函数，即声明当前函数作用域（上下文）

- 作用：隔离变量

- 作用域链：变量在创建函数的作用域取值。没查到就去上级查，直到全局作用域。这个查找的过程链

- 变量

  |          | var  | let  | const |
  | -------- | ---- | ---- | ----- |
  | 块       | ❌    | ✅    | ✅     |
  | 先声明   | ❌    | ✅    | ✅     |
  | 重复声明 | ✅    | ❌    | ❌     |

  建议用let，const块级作用域替代闭包

# 闭包

- **定义**：一个函数有权访问另一个函数作用域的中变量

​	js变量作用域属于函数作用域，函数执行完，作用域会被清理，内存被回收。

​	but 闭包的函数是建立在内部子函数（闭包）上，它可以访问上级作用域，上级执行完，作用域也不会被清理。 

- **特性**

  可以访问定义它们的外部变量

  保护：区域中私有变量不受外界影响，避免全局变量污染

  保存：将外部作用域中变量存储在内存中，而非函数

- **缺点**：内存泄露

- 实现

  函数嵌套。eg：一个函数的返回值是另一个函数，即函数和它的执行环境形成了一个闭包

  ```
  function addFn() { 
  	let a = 1;
  	return function () {a++; return a;} 
  }
  let newFn = addFn();
  ```

  内部函数引用外部函数局部变量，延长外部变量生命周期

  <img src="/Users/burst/Library/Application Support/typora-user-images/image-20250528145910084.png" alt="image-20250528145910084" style="zoom:25%;" />

- 用途

  模仿块级作用域

  封装私有化变量

  **节流**：控制事件触发频率

  ```
  function throttle(fn, wait) {
  	let flag = false;
  	return function () {
  		if (flag == false) {
  			flag = true
  			timer = setTimeout(() => {
  				fn();flag = false;
  			}, wait);                
  		}           
  	}        
  }
  ```

  防抖：事件触发后，应在一定的时间后才能生效

  ```
  function debounce(callbackFn, interval) {
  	var flag = null            
  	return function () {                
  		clearTimeout(flag)                
  		flag=setTimeout(()=>{callbackFn()},interval)
  	}        
  }
  ```

  

# 垃圾回收

- why：内存不释放，页面性能会变慢。即内存泄漏（全局变量、闭包、Dom元素引用、定时器）

- 浏览器有垃圾回收机制，定期找出不继续使用的变量来释放

- method: 
  - 标记清除：从根对象开始，递归标记所有可达对象。清除未被标记的对象（即不可达对象）。

  - 标记整理算法（优化版标记清楚）：在清除阶段后，将存活对象移动到连续内存空间，避免碎片

  - 分代回收算法：新对象分配在新生代（短期对象（如局部变量），回收频繁）；多次回收后仍存活的对象晋升到老生代；对老生代采用更高效的标记整理算法

- 优化：手动释放，内存优化，取消占用内存


# 普通函数/箭头函数/new

- 箭头函数

  - 无this，可从上层作用域继承

  - this指向不变，不会因为谁调用改变

  - 不能new构造对象

  - 无arguments

  - 无prototype

- new

  - 生成对象

  - this指向该对象

  - 执行构造函数

  - 返回该对象

  ```
  // 手写new
  const newInstance = (fn, ...args) => {
    const obj = Object.create(fn.prototype) // 创建一个新对象，继承构造函数的原型
    const res = fn.apply(obj, args) // 将构造函数的this指向新创建的对象，并传入参数
    return res instanceof Object ? res : obj // 如果构造函数返回的是一个对象，则返回该对象，否则返回新创建的对象
  }
  ```

  

# useStrict

1、禁止使用未声明变量，重复声明 

2、禁止删除变量 

3、this是undefined

4、只读属性不能赋值 

5、防止不安全才做 

6、严格解析

# 柯里化

将多参数函数转换为一系列单参数函数的技术，将f(a, b, c) 转换为 f(a)(b)(c) 

```javascript
function curry(fn) {  
	return function curried(...args) {    
		if (args.length >= fn.length) { // 参数够了，执行原函数      
      return fn(...args);    }
		else { // 参数不够，返回新函数继续收集      
			return function(...moreArgs) { return curried(...args, ...moreArgs); };    
    }  
  };
}
const add = (a, b, c) => a + b + c;
const curriedAdd = curry(add);
//curriedAdd(1)(2)(3)，curriedAdd(1, 2)(3)，curriedAdd(1)(2, 3)
```

# 数组操作类型常用方法

| **分类**        | **方法及示例**                                               |
| --------------- | ------------------------------------------------------------ |
| **创建**        | [], Array.of(num), Array.from(string或{ length: 3 }, (_, i) => i) |
| **访问**        | [], at(), indexOf(), includes(), find()                      |
| **修改**        | **push(), pop(), shift(), unshift(), splice()**   `array.splice(start, deleteCount, item1, item2, ...);` |
| **遍历**        | for, for (const item of arr)  ，arr.forEach((item, index, array) =>{}) |
| **转换**        | map(), filter(), 累加reduce(), 扁平flat(), flatMap()先 map 再 flat.       //[1, 2, 3].reduce((acc, curr) => acc + curr, 0);       nested.flat(Infinity).    ["Hello world", "Goodbye "].flatMap(s => s.split(' '))` |
| **查找 / 判断** | arr.indexOf()索引，arr.includes()返回true;<br/>every(), some()至少一个,arr.find(x => x > 25)第一个满足元素，arr.findIndex(x => x > 25)索引 |
| **排序 **       | **sort(), reverse()**                                        |
| **合并 / 分割** | concat(), slice(), 展开语法 [...arr]  例merged.slice(2, 5); // 从索引2到5（不包含5） |

# 对象操作

**`Object.keys(obj)`**：自身可枚举属性名

**```obj.hasOwnProperty(key)```**:判断对象属性

**`Object.getOwnPropertyNames(obj)`**:获取对象自身所有属性名

**`Object.defineProperty(obj, 'b', { value: 2, enumerable: false });`**:设置对象属性



# 遍历for

| **方法**       | **速度（大致排序）**   | **可中断性**                                       | **适用数据结构**             |
| -------------- | ---------------------- | -------------------------------------------------- | ---------------------------- |
| **for 循环**   | 最快                   | ✅ `break`（完全终止）和 `continue`（跳过当前迭代） | 数组                         |
| **for...of**   | 较快                   | ✅                                                  | 可迭代对象（数组、Set、Map） |
| **forEach**    | 中等                   | ❌return仅跳过当前回调，无法终止循环                | 数组                         |
| **map/filter** | 较慢（需创建新数组）   | ❌                                                  | 数组                         |
| **for...in**   | 最慢（**遍历原型链**） | ✅                                                  | 对象                         |

**Object.entries()**：返回 `[key, value]` 对的数组

**Object.keys()**：返回[key]数组

# Object.

|                                                  | 含义                                                         | 备注                                                         |
| ------------------------------------------------ | ------------------------------------------------------------ | ------------------------------------------------------------ |
| **Object.assign(target, ...sources)**            | 对象中所有[可枚举](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Object/propertyIsEnumerable)的[自有属性](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Object/hasOwn)复制到目标对象 | 原型链属性不可以拷贝                                         |
| **Object.create(proto, propertiesObject)**       | 以一个现有对象作为原型，创建一个新对象                       | 实现继承<br />propertiesObject 可以是{   // foo 是一个常规数据属性   foo: {     writable: true,     configurable: true,     value: "hello",   }} |
| **Object.defineProperty(obj, prop, descriptor)** | writable: 可修改<br />configurable：false。不可配置但可写的数据属性可以改，其它都不能改<br />enumerable： false；//obj.key2 undefined | Object.defineProperty(obj, "key2", {   enumerable: false,   configurable: false,   writable: false,   value: "static", }); |
| **Object.entries(obj)**                          | 静态方法返回一个数组，包含给定对象自有的可枚举字符串键属性的键值对。<br />Object.entries({a:1,b:2})<br />[ ["a",1], ["b", 2]] | 字符串Object.entries("foo"); // [ ['0', 'f'], ['1', 'o'], ['2', 'o'] ]<br />其它基本类型返回[] |
| **Object.freeze(obj)**                           | 不能再被更改：不能添加新的属性，不能移除现有的属性，不能更改它们的可枚举性、可配置性、可写性或值， |                                                              |
| **Object.fromEntries()**                         | 键值对列表 转 对象                                           | const map = new Map([  ["foo", "bar"],   ["baz", 42], ]); <br />const obj = Object.fromEntries(map);<br />// { foo: "bar", baz: 42 } |
| **Object.getOwnPropertyNames(obj)**              | 可枚举和不可枚举属性的名称，返回字符串数组                   | const arr = ["a", "b", "c"]; console.log(Object.getOwnPropertyNames(arr).sort()); // ["0", "1", "2", "length"] |
| **Object.keys(obj)**                             | 可枚举的字符串键属性键组成的数组                             |                                                              |
| **Object.values(obj)**                           | 可枚举字符串键属性值组成的数组                               |                                                              |

# CSS

## 三栏布局

- flex

- grid

```html
display: grid;
grid-template-columns: 200px 1fr 150px; /* 三列布局 */
```

- 浮动

  ```
  .float-container {
    overflow: hidden; /* 清除浮动 */
  }
  
  .left {
    float: left;
    width: 200px;
  }
  
  .right {
    float: right;
    width: 150px;
  }
  
  .main {
    margin-left: 210px; /* 左侧栏宽度 + 间距 */
    margin-right: 160px; /* 右侧栏宽度 + 间距 */
  }
  ```

  

## 获取元素位置

```javascript
const element = document.getElementById('myElement');  //getElementsByClassName,querySelector
var rect = element.getBoundingClientRect();
top: rect.top + window.scrollY,
right: rect.right,
bottom: rect.bottom,
left: rect.left + window.scrollX
```

## 判断是否是子元素

```javascript
// a在b内部
const isChild = b !== a && b.contains(a); //true✅
const relationship = b.compareDocumentPosition(a); //16在
function isChildOf(a, b) {
  let current = a;
  while (current) {
    if (current === b) return true;
    current = current.parentElement;
  }
  return false;
}
const isChild = a.closest('#b') === b; // 假设 b 的 ID 是 'b'
```

## 水平垂直居中

![img](https://api2.mubu.com/v3/document_image/28886397_4bb484cd-aa3f-4f86-f132-db99265d8c14.png)

## flex

**flex: 1**

```
flex-grow: 1;    /* 允许元素增长以填充可用空间 */大的占的比例大
flex-shrink: 1;  /* 允许元素缩小以适应容器 */0不缩
flex-basis: 0%;  /* 元素的初始大小为 0 */
```

- 容器6个属性
  - flex-direction属性决定主轴的方向
  - flex-wrap 是否换行
  - flex-flow 是上面两个的缩写
  - justify-content属性定义了项目在主轴上的对齐方式。
  - align-items属性定义项目在交叉轴上如何对齐。
  - align-content属性定义了多根轴线的对齐方式。如果项目只有一根轴线，该属性不起作用。
- 项目的6个属性
  - order属性定义项目的排列顺序。数值越小，排列越靠前，默认为0。
  - flex-grow 放大比例 默认为0，即如果存在剩余空间，也不放大。
    - 如果所有项目的flex-grow属性都为1，则它们将等分剩余空间（如果有的话）。如果一个项目的flex-grow属性为2，其他项目都为1，则前者占据的剩余空间将比其他项多一倍。
  - flex-shrink 缩小比例 默认为1，即如果空间不足，该项目将缩小。
    - 如果所有项目的flex-shrink属性都为1，当空间不足时，都将等比例缩小。如果一个项目的flex-shrink属性为0，其他项目都为1，则空间不足时，前者不缩小
  - flex-basis 分配多余空间之前，项目占据的主轴空间.
    - 浏览器根据这个属性，计算主轴是否有多余空间。它的默认值为auto，即项目的本来大小。
  - flex 上面三个的缩写 默认值为0 1 auto。后两个属性可选。
    - 该属性有两个快捷值：auto (1 1 auto) 和 none (0 0 auto)。
  - align-self 允许单个项目有与其他项目不一样的对齐方式。可覆盖align-items属性。默认值为auto，表示继承父元素的align-items属性，如果没有父元素，则等同于stretch。

## css 选择器的优先级

!important > 行内样式 > id选择器 > 类选择器 > 标签选择器 > 通配符选择器 > 继承 > 浏览器默认样式

| **选择器类型**   | **权重值** | **示例**                   |
| ---------------- | ---------- | -------------------------- |
| **内联样式**     | `1000`     | `<div style="color: red">` |
| **ID 选择器**    | `100`      | `#header`                  |
| **类选择器**     | `10`       | `.container`               |
| **属性选择器**   | `10`       | `[type="text"]`            |
| **伪类选择器**   | `10`       | `:hover`, `:nth-child(2)`  |
| **元素选择器**   | `1`        | `div`, `p`                 |
| **伪元素选择器** | `1`        | `::before`, `::first-line` |
| **通配符选择器** | `0`        | `*`                        |
| **继承的样式**   | `无权重`   | 由父元素继承的样式         |

多个结合使用：累加

相同：后定义的优先级高

## 行内标签、块内标签

**块标签：div p h1-h6 hr ul ol li dl dd dt form** 

​      ①支持宽高，自上而下排列

​      ②不受空格影响

​      ③一般用于其他标签的容器

​      ④默认宽度为100%（独占一行）。

**行内标签：span i a b strong em sub sup u label br font**

​       ①不支持宽高（宽高根据内容大小自动撑开），自左向右排列

​       ②受空格影响

​       ③不独占一行

**行内块标签：img  textarea  input**

​        ①支持宽高，自左向右排列

​        ②受空格影响

​        ③不独占一行

**标签之间的转换**

display：inline（转为行内元素）

​       inline-block（转为行内块元素）

​       block（转为块元素）

​       none（隐藏 不显示）

注意：当元素浮动（float）时会转化成行内块元素特点。

## **position属性值**

1. **static**（默认值）：正常文档流，`top`、`right`、`bottom`、`left` 和 `z-index` 属性无效。
2. **relative**：正常文档流，通过 `top`、`right`、`bottom`、`left` 调整位置，相对于其正常位置偏移。可设置 `z-index` 
3. **absolute**：脱离文档流，定位相对于最近的**已定位祖先元素**（relative`、`absolute`、`fixed` 或 `sticky），同2.
4. **fixed**：脱离文档流，定位相对于**浏览器视口**，同2。用于实现固定导航栏、悬浮按钮等。
5. **sticky**：正常文档流，滚动到特定位置时变为固定定位。必须有`top`、`right`、`bottom`、`left`。用于实现粘性标题、侧边栏

## 伪元素、伪类

| **对比维度**     | **伪元素**                                                   | **伪类**                                                     |
| ---------------- | ------------------------------------------------------------ | ------------------------------------------------------------ |
| **本质**         | 创建虚拟元素（文档树外）                                     | 描述元素状态 / 位置（文档树内）                              |
| **语法**         | 使用 **双冒号 `::`**（CSS3 规范）                            | 使用 **单冒号 `:`**                                          |
| **数量**         | 一个选择器中最多使用 **1 个伪元素**                          | 一个选择器中可叠加多个伪类                                   |
| **操作对象**     | 操作元素的**部分内容或虚拟内容**                             | 操作元素的**整体状态或位置**                                 |
| **是否生成内容** | 可生成新内容（如 `::before`/`::after`），必须设置 content 属性 | 不生成新内容，仅匹配状态                                     |
| **常见用途**     | - 清除浮动（`::after`） - 添加装饰性内容 - 操作文本首字母 / 行 | - 交互状态（`:hover`/`:focus`） - 结构伪类（`:nth-child`） - 动态状态（`:disabled`） |

## BFC

**BFC（Block Formatting Context）** 是 CSS 中一种独立的渲染区域，它规定了内部元素如何布局，以及与外部元素的交互规则。

解决常见的布局问题（如高度塌陷、外边距重叠等）。

**触发 BFC 的条件**

1. **浮动元素**：`float` 值为 `left`/`right`（非 `none`）。
2. **绝对定位元素**：`position` 值为 `absolute`/`fixed`。
3. **行内块元素**：`display` 值为 `inline-block`。
4. **表格相关元素**：`display` 值为 `table-cell`/`table-caption` 等。
5. **overflow 非默认值**：`overflow` 值为 `auto`/`scroll`/`hidden`（非 `visible`）。
6. **弹性 / 网格容器**：`display` 值为 `flex`/`grid` 及其衍生值的直接子元素。

## 高度坍塌

发生在父元素包含浮动（float）子元素或绝对定位（absolute/fixed）子元素时，父元素无法正确计算高度，导致布局混乱

解决：清除浮动clear:both、BFC、使用flex

## **盒模型**

**标准盒模型**

- width就是content

**怪异盒模型（IE 盒模型）**

- width=content+padding+bording

- 适合固定宽高的布局（如响应式设计）

- ```
  box-sizing: border-box
  ```

## 1px问题

问题：高清设备的设备像素比 DPR是2或3，造成1px会渲染2或3个物理像素

1、transform: scale

```html
/* 适配 设备像素比 DPR=2 的设备 */
@media (-webkit-min-device-pixel-ratio: 2) {
  .element::after {
    transform: scale(0.5);
  }
}
```

浏览器不支持小数，所以0.5px也会是1

2、`viewport`，全局生效可能会有布局错乱问题；需要动态计算 DPR 并调整 `viewport`，兼容性较差

```
<meta name="viewport">` 的 `initial-scale
DPR2的是initial-scale=0.5
```

# Typescript

添加静态类型、类、接口和 模块 等功能，更容易进行维护和扩展

> **概念**
>
> 类型声明：显示指定类型
>
> 类型推断：ts根据赋值推断
>
> 枚举：命名常量的一种方式 enum Mytype{}，比对象映射严格。
>
> 联合类型：一个值可以是多个类型中一种。 ｜
>
> 交叉类型：包含多个类型特性。 &



## type和interface

| **特性**            | **`interface`**接口：定义了契约，可在多地共享 | **`type`**类型别名：给一个类型起名字，多地使用 |
| ------------------- | --------------------------------------------- | ---------------------------------------------- |
| 重复定义合并        | ✅（自动合并）                                 | ❌（报错）                                      |
| 定义基本类型        | ❌                                             | ✅（如 `type ID = string`）                     |
| 定义联合 / 交叉类型 | ❌                                             | ✅（如 `type A = B & C`）                       |
| 类实现              | ✅                                             | 仅支持对象类型的 type                          |
| 扩展方式            | `extends`                                     | 交叉类型 `&`                                   |
| 映射类型 / 条件类型 | ❌                                             | ✅                                              |

## 泛型 & any & unknow

**泛型T**：允许在定义函数、类或接口时不预先指定具体类型，而是在使用时动态传入类型。增加代码的灵活性和重用性。

**any**：任何类型，不推荐

**unknow**：any的安全写法，使用前先校验类型

**泛型和any区别**：保持类关联信息，传入和返回类型关联。any不校验。

```javascript
function printName<T extends { name: string }>(obj: T) {  
	console.log(obj.name); // 确保 obj 有 name 属性 
}
```

## 数据类型

基本类型：number,  string, boolean, null, undefined, symbol

复合类型：array, tuple（元祖：固定数量和类型的数组）, enum

对象类型：object, interface 

函数类型：function, void, any

高级类型：联合，交叉



# 大文件上传

1、文件切片：切成5-10M，文件数组是[{index,data, hash}]

```
// 文件分片伪代码
const chunkSize = 5 * 1024 * 1024; // 5MB
let offset = 0;
while(offset < file.size) {
  const chunk = file.slice(offset, offset + chunkSize);
  chunks.push({
    index: offset / chunkSize,
    data: chunk,
    hash: await calculateHash(chunk) // 计算分片哈希
  });
  offset += chunkSize;
}
```

2、实现断点续传：  上传前计算每一块的hash。然后向服务端查询进度，已经上传的hash。最后仅上传确实部分hash文件。

```
// 检查上传进度伪代码
const response = await api.checkUploadProgress(fileHash);
const missingChunks = chunks.filter(c => !response.uploadedIndexes.includes(c.index));
```

3、并发控制和上传优化：设置3-5并发上传通道，自动重试失败分片，提供暂停继续功能。

优化：可以根据网络环境动态分片大小。服务端合并分片进行完整性校验


# 小程序
问题:
1原生组件css差异(比如按钮)
解法:需要根据渲染引擎写不同css进行适配
2skyline rpx到px有精度问题，与webview有差距
解法:其中对于webview精度优化增加covertrpxtovw。skyline可能也需要适配
3 判断当前渲染引擎(版本支持+ab)
解法:getSkylinelnfoSync
4 自定义组件不支持v-show
解法:页面中大量出现，更改方式外层套视图，风险较大，整体样式(webview+skyline)应该都需要兼容
## uniapp和原生差距
1. **核心定位不同**：
   - UniApp是**跨平台框架**，解决多端重复开发问题
   - 原生开发是**平台定制方案**，追求极限性能和深度集成

2. **技术差异**：
   - 开发语言：Vue vs 平台DSL
   - 性能：原生更优但UniApp可达90%原生体验
   - 生态：UniApp有uView等跨端组件库

3. **选型建议**：
   - 中小项目/快速验证 → UniApp
   - 重度依赖平台能力/性能敏感 → 原生
<img width="802" alt="image" src="https://github.com/user-attachments/assets/8a703d93-34f7-4f74-a111-ddf69cfbfd0b" />

<img width="794" alt="image" src="https://github.com/user-attachments/assets/220eff30-6dc4-4213-a5c2-85b555c605be" />
