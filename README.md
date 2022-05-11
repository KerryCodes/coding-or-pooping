# coding-or-pooping
![如何把前端项目写成一座屎山？](https://juejin.cn/post/7086735198942920712)


## 前言

最近几年前端发展的非常快，SPA的繁荣让前端的工程化也越来越重。在很多场景下，前端的复杂度和难度也早已经超过了后端。但快速的发展下，前端也逐渐暴露出了许多问题。众所周知，前端从业人员很少谈程序的设计原则或设计思想。设计模式也顶多是在八股面试时千篇一律的问答“观察者模式”和“发布订阅者模式”。“内聚”和“解耦”这样的词语也很少从前端嘴里蹦出。这就难免导致前端代码写成一座大屎山。而这还是在基于类MVVM框架开发模式的前提下，前端代码天然具有了组件级别的抽象，如果是刀耕火种的MVC时代，更是难以想象。

同事负责的一个前端项目频频爆出bug，已经到了修1个bug产生3个bug的程度，甚至很多bug无法定位。问了同事原因，回答项目比较复杂。窃以为项目复杂不是写成屎山的理由（举一个极端的例子，你的项目再难再复杂也不会超过Chrome浏览器，那如果Chrome浏览器项目可以被维护的非常得体，难度更低的项目一定也能找到好的技术方案和架构来应对。）。出于好奇大致浏览了这个项目的代码，发现这就是一座典型的前端大屎山。除了作者本人应该没有任何人可以或愿意接住该项目，未来的命运就只能是招个新人从0开始重构，甚至一行代码都没法参考（我经历过这事！）。

纯粹从编写软件的角度，其实目前有很多成熟的代码规范可以参考，甚至规范到变量命名等等。但这里我们暂且只讨论前端这个领域的屎山堆积技巧。


## 精华教程

- **拒绝Ts**
坚决不用Ts，甚至将Ts写的项目重构成Js代码。去年我被空降了一个leader（多年前就是阿里P7级别）。在看了一眼我维护的富文本编辑器项目之后，告诉我需要重构该项目，重构目标是抛弃Ts，用Js重写。我在纠结了好几天之后，做出了一个艰难的决定。。。

---

- **拒绝hooks**
所有组件都用Class组件，拒绝函数组件，拒绝hooks。

---

- **全面拥抱状态管理器**
所有状态都通过类似Redux或Mobx等状态管理器去管理。

---

- **不做模块抽象和复用**
每个功能都从0开始实现，不抽象任何公共组件，不把高频出现的逻辑抽象成hooks，不抽象出工具函数，坚决不复用任何逻辑。

---

- **把JSX结构掰开揉碎**
直接在JSX上写长函数和复杂参数，至少需要达到一眼看上去稀碎，完全无法在脑中构建出页面的样子。

---

- **编写长长长长长的组件**
一整个页面只编写1个组件去维护，单个组件代码行数轻松写到1000行以上。

---

- **父子组件多传参，尽可能多层传递**
父组件给子组件传非常多参数，然后子组件继续又将这些参数层层往下传递。

---

- **单文件开发**
将状态、数据、类型、工具函数、网络请求和组件等等全部放入一个文件中。

---

- **打破文件组织结构与组件结构关系**
虽然组件天然是一个多叉树结构，但相应的文件全部平铺到1层。

---

- **不封装网络请求函数**
每次请求都创建新的Axios实例，网络请求错误不统一拦截，全部单独catch。

---

- **样式混用和强行覆盖**
内联样式与css文件样式混用和覆盖。类名随便起，不要透露结构信息，相同的css代码在各个类上直接复制黏贴一份。遇到冲突的样式强行再覆盖一层。

---

- **到处修改UI组件库内部样式**
为了达到设计要求，通过导出类名强行覆盖UI组件库的内部css样式，多用!important魔法。

---

- **多用Js代替CSS实现效果**
伪类伪元素等坚决不用，动画过渡等效果也必须通过Js实现。

---

- **到处使用微前端**
尽可能的把页面拆成一个个单一功能的微前端应用。

---

- **不要argue需求**
对于产品或设计给到的需求全盘接受，尽力实现交互复杂混乱繁冗的功能，获得技术成就感，做一只不挑食的小白兔。

---

- **评论区补充xdm看家绝技，闻者落泪**

![Jietu20220418-173720.jpg](https://p9-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/47257a038ef1445786f9d8d530961901~tplv-k3u1fbpfcp-watermark.image?)

![Jietu20220418-173819.jpg](https://p1-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/b023475ebf574509bcc7bce664a11d12~tplv-k3u1fbpfcp-watermark.image?)

![Jietu20220418-173901.jpg](https://p1-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/f063d7e1cf454eeca4a8fbf7777773a5~tplv-k3u1fbpfcp-watermark.image?)

![Jietu20220418-174042.jpg](https://p1-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/0dbb2c503ddb4af78ecd2afa903e99d3~tplv-k3u1fbpfcp-watermark.image?)

![Jietu20220420-111451.jpg](https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/cf0e7843870541c69b0f1f5e0f9edaee~tplv-k3u1fbpfcp-watermark.image?)

![Jietu20220420-161649.jpg](https://p6-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/3f7890c615604cbb8ae13b9c29d31eda~tplv-k3u1fbpfcp-watermark.image?)

![Jietu20220421-113743.jpg](https://p9-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/d2800e5e2a1e4243a3f61f7c2da9aef4~tplv-k3u1fbpfcp-watermark.image?)

![Jietu20220421-171232.jpg](https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/50dd9e3f12b44c1f94d4b441b1098782~tplv-k3u1fbpfcp-watermark.image?)

![Jietu20220422-141525.jpg](https://p1-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/0c40f7a96dd94473ab411f79a8f3330a~tplv-k3u1fbpfcp-watermark.image?)

![image.png](https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/03567cd2c4314811944ed897e86a4020~tplv-k3u1fbpfcp-watermark.image?)

![image.png](https://p1-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/50aa14e64b31423998e75b1b9511556b~tplv-k3u1fbpfcp-watermark.image?)

![Jietu20220509-160401.jpg](https://p9-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/8303d84459484204ba14801621a62e72~tplv-k3u1fbpfcp-watermark.image?)

![Jietu20220509-160457.jpg](https://p6-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/541be4f709fc406c821b2ff1a39dbad8~tplv-k3u1fbpfcp-watermark.image?)

![Jietu20220509-160417.jpg](https://p9-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/67dabbb7f7d6452389dc58129e1ee50f~tplv-k3u1fbpfcp-watermark.image?)


## 收益

- 每次提交上线，产品测试后端都围着你充当鼓励师，唯恐出现生产事故大家一起背3.25警告。
- 每天都看起来非常忙，大家排队求你分一点时间处理各种技术问题，都哭着叫你大佬，饱受尊敬。
- 老板对你印象深刻，认为是个技术牛逼的救火队员，夸你勤奋不摸鱼下班晚，周报总是满满当当。
- 公司地位无可撼动，除了你这个项目没人有能力或愿意接住，只能给你加钱，生怕你离职。

> **一则旧闻**
>
> 魏文王问扁鹊：“你们家兄弟 3 人，都精于医术，到底哪一位最好呢 ? ”\
> 扁鹊答：“我的大哥医术最好，二哥次之，我最差。”\
> 文王再问：“那么为什么你最出名呢 ? ”\
> 扁鹊答道：“我大哥治病，是治病于病情发作之前的时候，由于一般人不知道他能事先铲除病因，反而觉得他的治疗没什么明显的效果，所以他的名气无法传出去，只有我们家的人才知道。我二哥治病，是治病于病情初起的时候，看上去以为他只能治轻微的小病，所以他的名气只能在我们乡里流传。而我扁鹊治病，是治病于病情已经严重的时候。一般人看到我在经脉上穿针放血，在皮肤上敷药，用麻药让人昏迷，做的都是些不可思议的大手术，自然以为我的医术高明，因此名气响遍全国，远远大于我的两位哥哥。”


*xdm，还有什么堆屎效果奇佳的好手段？可以issue补充啊！*
