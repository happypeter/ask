# Happypeter 每日一答

## 2017.2.6


http://haoduoshipin.com/v/210

## 2017.2.5：ES6 模块的最基本的使用方式是什么？

历史上，JavaScript 一直没有模块（module）体系，无法将一个大程序拆分成互相依赖的小文件，再用简单的方法拼装起来。其他语言都有这项功能，比如 Ruby 的 require、Python 的 import，甚至就连 CSS 都有 @import，但是 JavaScript 任何这方面的支持都没有，这对开发大型的、复杂的项目形成了巨大障碍。

在 ES6 之前，社区制定了一些模块加载方案，最主要的有 CommonJS 和 AMD 两种。前者用于服务器，后者用于浏览器。ES6 在语言标准的层面上，实现了模块功能，而且实现得相当简单，完全可以取代现有的 CommonJS 和 AMD 规范，成为浏览器和服务器通用的模块解决方案。

模块功能主要由两个命令构成：export 和 import 。export 命令用于规定模块的对外接口，import 命令用于输入其他模块提供的功能。来看一个 Hello World 级的例子。


先写一个 user.js


```js
let name = 'Peter';
export { name };
```

上面的文件中有 export 语句，那么这个文件可以被叫做一个 ES6 模块。那么在 index.js 中可以这样来使用这个模块：

```js
import { name } from './user';
console.log(name);
```

比较麻烦的步骤可能就是编译了，需要搭建一下 Webpack-babel 的环境，参考 [好奇猫上的课程视频](http://haoqicat.com/webpack-react-tricks/)

```
npm run build
```

就可以得到 dist/bundle.js 文件了。

```
$ node bundle.js
Peter
```

可以看到正确的输出。粗略的可以认为 bundle.js 就是 index.js 和 user.js 的合体。


## 2017.2.4：如何在微信公众号中使用 Markdown？

微信公众号后台发文章的时候，可以有一些简单的格式使用，但是，如果想插入代码等其他更加丰富的格式，就可以使用 Markdown 来排版了。

其实窍门就在于微信后台的编辑框中是可以直接粘贴 html 的，当然真正写文章的时候我们写的是语法更为简单的 markdown ，然后借助一个软件叫做 [markdown here](http://markdown-here.com/) 来把内容转化成 html 。

**markdown here** 可以作为一个 Chrome 的插件来安装。装好之后，打开微信发文章的位置，安装 markdown 语法输入自己的内容，然后点 Chrome 浏览器上方的 **markdown here** 的图标，就可以转换了。

具体操作视频里有：http://haoduoshipin.com/v/208

参考[半撇私塾的相关视频](http://learn.bpteach.com/open/course/1?utm_source=zhihu.com&utm_campaign=cnm-vol-01&utm_medium=social&utm_term=markdown&utm_content=wechat-layout-guide)

## 2017.2.3：ES6 的 let 和 ES5 的 var 有啥区别？

@me：ES6 的 let 和 ES5 的 var 有啥区别？

@happypeter： ES6新增了 let 命令，用来声明变量。它的用法类似于 var ，但是所声明的变量，只在 let 命令所在的代码块内有效。


```js
{
  let a = 10;
  var b = 1;
}

a // ReferenceError: a is not defined.
b // 1
```

上面代码在代码块之中，分别用 let 和 var 声明了两个变量。然后在代码块之外调用这两个变量，结果 let 声明的变量报错，var 声明的变量返回了正确的值。这表明，let 声明的变量只在它所在的代码块有效。`ReferenceError: a is not defined.` 的中文意思是：引用错误：a 没有定义。

总之，使用 let 更加安全，直观，而如果使用 var 就需要提防“变量提升”等各种恶心问题。所以最后的建议是，只要有 ES6 环境，尽量使用 let 。

更多细节请参考：http://es6.ruanyifeng.com/#docs/let


## 2017.2.2：《摩登前端开发者》的大纲在哪？

@me：《摩登》课程大纲在哪里？整理大纲的思路是什么？

@happypeter： 课程大纲整理到了 https://happypeter.github.io/qd/ 。

学习 Web 开发，资料永远不缺，但是问题可能就在于 Web 开发的技术点太多资料太多，新手于是也更容易走弯路。《摩登》课程力求一条最简单最直接的道路，让新手能用专业化的工具做出专业化的产品。一旦做完一个完整的项目，新手建立起了对知识体系的认识，后续再去学习各种资料也就会知道如何取舍了。


课程力求让大家掌握的是以下几点：

- 第一，知道各个基础工具如何提升项目开发的效率： Git 版本控制，Bash 命令行，Atom 编辑器

- 第二，理解前后端分离的架构：前台用 API 请求后台 Express 服务器

- 第三，掌握组件化开发界面的思想：使用 React + Redux + Webpack

- 第四，Web API 请求数据策略：Axios 工具使用，相关 HTTP 基础知识

- 第五，基本的 JS 开发能力：函数，面向对象，ES6

- 第六，数据库操作： MongoDB

- 第七，会自己动手制作 Web 应用的常见功能：登录，权限控制，增删改查





## 2017.2.1：《摩登前端开发者》互动课程的授课方式是怎样的？

@me：《摩登前端开发者》这几天正准备开第十一期，那么具体的授课内容和授课方式都是怎样的呢？

@happypeter： 《摩登》课程的授课目标有两个，一个是使用 React 技术开发 Web 应用，目标平台是各个浏览器，第二个是微信小程序开发，目标平台当然就是微信。之所以二者放在一门课程中去开，是因为二者技术上本身区别就不大，有了 React 开发能力的人，开发微信小程序也能很快上手的。

《摩登》课程和好奇猫的服务模式是有明显差别的。

- 第一，《摩登》课程是一门大课，从前到后都是一个连贯的故事，通过一百多个逐步放出的视频，让新手最终成为一个能做出产品来的开发者。《好奇猫》的服务形式是一门门的小课程，观众根据自己的需要去有选择的学习。

- 第二，《摩登》课程的视频分多个阶段放出，每个阶段都会有代码任务，用来检验学习者有没有跟上课程进度。确保每个同学（至少80%的同学）都 on same page ，是我追求的目标。

- 第三，《摩登》课程的授课方式其实更类似于线下班授课。就是随时聆听学习者的反应，如果某个知识点大部分同学都没听懂，就意味着这个知识点要补充新的视频来进行详细的讲解，并且要加强针对这个知识点的互动答疑了。

- 第四，《摩登》课程会把命令行，Git，ES6 等等知识点编排到一条故事主线中去讲，每次引入一个新的知识点，都默认学习者是零基础的。这样做的好处是，初学者可以用最短的时间掌握各个工具和知识点的最重要的使用技巧，而且因为是伴随课程大案例的制作过程来学习的，会对各个工具在整个项目开发中发挥的作用有清晰的认识。当然，对于命令行，Git，ES6 这些知识点，好奇猫上都是作为独立的课程来讲的，显然会讲的更深更细。

总之，《摩登》课程更像我的线下课程的一个低价格的翻版，有些翻转课堂的味道。


## 2017.1.31：制作一套案例型的视频课程的基本步骤有哪些？

@me: 从脑子里面有一个主题，到实际录制成多章多节组成的一套案例型视频课程都有哪些步骤？

@happypeter：跟讲基础知识的课程（《跟 Peter 学 HTTP 》）和讲基础工具的课程（《 Atom 爱上 JS 》，《 Git 北京》)，还是有区别的，具体步骤如下：

- 第一步，选定主题之后，看看自己能不能做出一个吸引人的案例出来，要是连案例都不能引起大家的兴趣，那这个主题最好放弃。例如这两天我录制《微信小程序之吻》这个做案例就很容易，把 haoqicat.com 上原有的功能在微信里实现一遍，做成微信登录，微信支付等实用的功能，显然是非常具有参考价值的

- 第二步，开始拆分整个案例，每一节视频尽量只去实现一个小功能，这样每一节都能有一个非常清晰简单的标题，例如《微信小程序开发工具安装》

- 第三步，开始写每一节的文字稿，大标题之下，第一句话就是介绍一下这一集要实现的是个什么功能，对应视频录制的时候，上来就先演示一下这一集到底做成了什么效果

- 第四步，每一节的内容再分两三个部分来推进，每个部分都有一个清晰的标题。标题之下引领这一步分的详细的文字内容已经用到的代码

- 第五步，不管是每一节的题目，还是一节中的各个部分的标题，都要以动手为主线。理论知识的讲解完全服从于动手过程。实际中我发现，脱离动手，脱离实际效果演示，讲的理论知识越多，内容就越乱越不实用。

总之，整个过程是通过各级标题形成骨架，然后骨架之上丰富内容的时候，保证每一句话都实用，保证每一句话都不脱离动手主线，整套课程下来就是一个完整的动手做东西的故事了。


## 2017.1.30：haoqicat.com 愿景？

@me：haoqicat.com  要服务哪一个客户群体？怎么服务？最近一段时间都有哪些动作？

@happypeter: 这两天在老家，发现随着大家都吃饱了，老家农村的朋友们也都开始努力让自己的情怀落地，有个朋友做了健身房，虽然亏损很多，但是也依然在坚持，我见到他，给他竖大拇指加油了。

创业者最应该做的事情是解决客户的痛点，创业者最能投入自己感情去做的事情就是解决自己的痛点。对我自己来说，人生最大的痛点就是大学毕业找不到理想的工作。所以 haoqicat.com  也就是要服务那些跟我情况类似的大学本科生，以及初去职场的年轻开发者。

具体的方式还是我2010年的博客里写的”英语加代码”。我希望帮助大家做到的是流利的用英文和代码来表达自己。haoqicat.com 上的视频都是中文讲解的，但是会努力引导大家去读英文资料，拥抱英文世界的工程师文化。没有漂亮的文凭，但是如果真的有一技之长，也照样可以找到好工作。haoqicat.com  要帮助大家的不是学知识，而是学技能。学习技能最好的方式就是看老手怎么工作，所以 haoqicat.com 以视频课程为服务形式，带大家一起动手做东西。

2017年，我会录制更多的课程，逐步形成完整的零基础到 job ready 的学习路线图。对于haoqicat.com 可以看到网站上每日一更的视频。同时，《摩登前端开发者》以及我在秦皇岛这边的线下课上，我会进一步加强跟学习者的互动。不坐在学员旁边，不看他亲手做东西，我就很难知道到底他有哪些地方不明白，我有哪些地方没讲清楚。


## 2017.1.29：过年这几天都干啥咧？

@me：大年三十，初一初二每天都干点啥？

@happypeter: 三十下午就是包素饺子，我没包，去找写字写的好的二伯伯把我爸的名字填到”家誊”上。家誊就是一张大纸，过世三年，名字写在上面，常年挂在墙上，受供奉。然后我回家，约表弟过来聊天，他在我们县城搞中学辅导班，跟北京青果教育合作，搞翻转课堂。从小的朋友了，很多观点都聊的来，聊的非常开心。

三十晚上去族人家辞岁，一个爷爷的我们兄弟几个凑一伙，去各家串门，不给人磕头，给家誊或者天地君亲师的牌匾磕头。晚上十二点上供，院子里面摆一张桌子，放五盘饺子，点上香，蜡烛，烧纸完毕，我跟我弟弟就分别朝东西南北四个方向跪拜，然后放鞭炮，这个就叫上供，女性不参加。然后，把素饺子吃了，就去睡觉了。但是灯是整晚不熄的。

初一早上还得早起，要”拜年”。串的门口比昨晚多，这次会给长辈磕头的。我今年给两个长辈磕头了。三十年来最少的一次。然后就是去坟地，弟弟带了七箱开天雷去放，每箱四桶。家族里上百人一起，大家放火烧野草，往各个坟头放烧纸，我给爷爷奶奶烧了纸，然后就一直傻呆呆的在父亲的坟头前烧纸。

初一晚饭，跟我大哥二哥在我弟弟家聚餐的。

今天是初二，去了姑姑舅舅和姨家，明天回秦皇岛。


## 2017.1.28：现代化和现代性都是什么东西？

@me：Peter 那天你在班上说，河北的学生进入北京职场前，先要了解什么是现代化，以及年轻人都要有现代性，这都是啥意思？

@happypeter：我自己是河北农村的孩子，现在正在老家拜年。非常清晰的能感受到北京创业圈和老家农业文明下的文化差异。

现代化其实就是英国化的另外一个说法。德国法国也很不情愿的接受过这个过程。一次世界大战的时候，德皇威廉就说过，这是一次神圣王权跟一群小商贩之间的战争。所以现代化也只能算是一家之言，我不讨论英国文化牛还是我们华夏文明牛，但是不可否认我们的政府，银行系统，一切的上层建筑都是按照英国佬几百年前提出的这一套为蓝本的，所以了解现代化对于现代的职场人肯定是必要的。推荐阅读是《英国私有制起源》以及大宪章的诞生过程。我也是听了罗辑思维的几期节目，才想通了这个问题的。

那什么是我眼睛中的现代性呢？制度层面上就是英国的那套私人财产神圣不可侵犯的思路。道德层面上就是康德哲学的核心观点，人生唯一的悲剧就是屈从于他人的意志。康德的纯粹理性批判我也没读过，主要是通过哈佛的那套公开课《Justice 》来了解的。所以现代性的人应该是，把所有神圣的东西都挨个亵渎一遍的人，把所有锁链都杂碎的人。是理解自由平等的人，是对文艺复兴有充分了解，对个人欲望敢于张扬的人。

现代性是对传统思路的颠覆。昨天在家干点活，笨的要死，又被大伯呵斥了几句，从小就是这个样子，传统的父权思想我是很不喜欢，但是偶尔你看看《曾国藩家书》就可以理解他们长辈们的文化心理了。传统思路重视秩序，现代性就是个人大于集体，传统思路下人要自我实现就要当官，现代性的人应该有的是服务心态，传统思路下诸多禁忌，现代性就是当街接吻，性开放，传统思路就是服从权威，现代性就是自己为自己的行为负责。

## 2017.1.27：haoqicat.com 会员和《摩登前端开发者》的区别？

@me：已经有好奇猫年会会员了，为何年后还有《摩登前端开发者》第十一期？二者之间的区别？

@happypeter：首先介绍一下二者。

haoqicat.com 会员，服务期一年，费用一千元。可以观看 haoqicat.com 的所有课程，以及通过折扣价格获取其他我推出的各位其他服务。

《摩登前端开发者》费用600，服务期三个月。

说一下二者的几点区别。

首先，课程系统性。haoqicat.com 上面每日更新一个新视频，但是视频内容是随机的。《摩登》课程，是一整套的大课，分几个阶段发布，从简单到复杂，是一个新手可以步步跟进的故事。

第二个，课程答疑服务。好奇猫会员群里面我会跟大家做一些关于课程的讨论，但是没有系统的答疑服务。《摩登》课程只要跟课程相关的问题，我会全部回答，保证大家都能跟上进度，可以说对新手更友好。

第三个，《摩登》课程大概会有一百多个视频组成，差不多也是每日一更，随时跟学员互动答疑，后续视频也会根据大家的掌握情况进行难度的调整。《摩登》课程正在开课的内容不属于 haoqicat.com  ，会员也需要专门报名才能参加。费用只是非会员的六分之一，也就是100元。


## 2017.1.26：有啥好的音频节目可以推荐么？

@me：Peter 平时你都听那些音频节目？各个节目都都什么特点？

@happypeter：大学时候我属于那种买书最多的人，不过最近十年发现每天对着电脑看资料，眼睛挺累，所以很少看书了。开拓眼界不靠眼睛，现在主要靠耳朵。

历史故事感觉是毒药，但是跟鸦片一样，还是戒不掉。小时候受到的教育是以史为鉴，不读史，不知前人创业之艰辛，不知后人守成之不易。现在发现这些思想基本狗屁，历史基本就是故事，没有太多可信性，精华不是没有，糟粕还是主流。但是习惯就是习惯，消耗我业余时间最多的还是历史故事，《晓松奇谈》，《逻辑思维》还有袁腾飞我都特别喜欢。

现代教育的最大意义应该是让人能清晰思考，或者是掌握技能。《得到 App》上的《前哨王煜全》是我最近最喜欢的一个节目。主要介绍美国的先进科技动向给国内投资人。聊人工智能，无人驾驶，比特币，论述角度不是特别深入的技术层面，主要瞄准科技是如何改变社会结构的。《得到》上其他的节目也都很好，基本都是在培养现代人的。而且听起来都是有趣的，减压的，我没事的时候带上耳机，当故事会听。

袁腾飞，高晓松我都很喜欢，不过思想里面很多东西都是落后的。对于高科技，数字，逻辑，事实，这些东西缺乏透彻的理解和尊重。思想中蒙昧的东西很多。蔡康永是美国回来的大学生，他就对高晓松为啥那么喜欢历史表示不理解。为啥不去多了解一些当下的社会问题呢？再有时间，可以去培养各种技能呀，包括音乐，包括审美，体育。


## 2017.1.25：春节这几天如何安排？

@me：春节这几天都干什么？节后的安排是？

@happypeter：今天是阴历二十八了，今天照常有《 Happypeter 每日一答》，也会有《视频每日一更》。明天是二十九，也会有视频更新。三十，初一，初二，我就休假三天了。初四开始正常录视频，继续完成《小程序之吻》课程。

三十陪老妈聊天，初一上午拜年然后去上坟，下午在家跟老妈聊天。初二，去看姑姑舅舅这些亲戚，都是些从小就对我很好的最亲的人。不过现在见面也都没什么话题可以聊了，而且像我这样不买房子，不生孩子的人，在他们的价值体系中也不知道如何给我定位才好。

所以，过完年还是早点回秦皇岛，去年是初二回的，今年最晚初三回来。回来继续跟教练跑步，教练的每周三次约跑的训练计划春节期间也是完全不间断的。再就是我回来开始就要着手准备《摩登十一期》的课程了。


## 2017.1.24：年轻人最理想的工作是什么样的？

@someone：Peter ，最近拿了几个工作的 offer ，你觉得哪个最好呢？

@happypeter：先说什么样的是不好的。传统大公司的文化的工作都是不好的。因小而美的年代，Peter 建议大家都去小团队，当然，现在最优秀的互联网大公司，也都是小团队文化了，像阿里，google，facebook 等等都是很棒的。但是一些老牌的 IT 公司，就很恶心，到现在还在搞 KPI 那一套。

所以，最好的公司，应该是小团队（例如当初的微信团队，淘宝团队），没有官僚气氛，大家认认真真的在解决一个实实在在的客户痛点的公司。

公司里面的职位当然也有分别。我的感觉是现在是一个大变革的时代，前方的道路暂时看不清，不要指望你搞一个方向就吃一辈子。所以好的工作岗位应该是最能够培养你快速学习和沟通能力的岗位。你可能说，啊，这个说法感觉很对，但是执行起来好像没有方向哦？答案是，每天的执行都有很多硬功夫需要练，其中最重要的就是“泛语言能力”。

包括英文能力（帮助你更有效的学习），写文章能力（从古至今最有效的与人沟通的方式），演讲能力（感染他人），这几项都是跟人沟通的能力。但是最为一个摩登的人，还要学会跟机器沟通的能力，学习编程语言。我总说知识不重要，多年习得的技能（硬功夫）才能把你跟其他人才区分开，而最重要的硬功夫就是我前面提过的”泛语言能力“。而最好的工作我觉得也就是能最快速的培养你”泛语言能力“的工作。

## 2017.1.23：Nginx 服务器配置的课程有没有呢？

@焕哥：Nginx 服务器配置的课程有没有呢？

@happypeter：目前还真的没有。我的思路是这样的，作为全栈开发者，我们不但要有能力把代码写好，还要有能力把代码部署到服务器上真正运行起来。

把一份本地开发调试好的代码变成一个在线的网站，要经历下面的几个步骤：

- 申请域名
- 申请服务器（阿里云等）
- 域名绑定
- 代码上传（现在一般直接用 github 克隆）
- 服务器进程管理（ tmux service pm2 Linux 启动脚本）
- Nginx 服务器配置（反向代理，创建多个 server ）

对于咱们来讲，咱们不是系统管理员，不需要对上面各个步骤，包括 Nignx ，非常的专业，但是起码一些常用技巧也都应该会的。

http://www.haoduoshipin.com 上关于**部署**相关的视频里都会或多或少的提到一些 Nginx 的知识，但是目前比较系统的关于部署的课程的确还没有，后面我会积极考虑制作一门的。





## 2017.1.22：Vue.js 会超过 React 吗？

@someone：Vue.js 会超过 React 吗？

@happypeter：根据 https://risingstars2016.js.org/ 上的统计数据，从 github star 数目来看，2016年 Vuejs 比 React 的发展快一些。当然 React 的总的社区还是大很多，从 npm 下载量上可以看出来。

我对 Vue.js 一直在关注，但是没用过，那天跟用 Vue 的朋友请教 Vue 的优势，其中比较重要的一点就是，Vue 上手还是比较容易。举例来说，如果直接一个 html 页面中用 script 标签引入 Vue ，就可以做很多效果出来了，但是如果引入 React 就比较麻烦，React 还是配合 Webpack 来用比较好，但是有了 Webpack 这一套，复杂度就上来了。Vue 跟 React 很像，但是相比之下 Vue 很微信小程序的相似度更高。另外 Vue 相当大的一个优势就是中文文档比较丰富。这个对于编程新手也是友好的。

Vue.js 能不能超过 React 我也不太关心，因为二者毕竟也是很像，切换成本没那么高，我等等看。年后，第一门课先弄微信小程序。


## 2017.1.21 人工智能会带来怎样的未来？

@B：Peter 你也扯扯未来是什么样的把？人工智能都火成这样了。

@happypeter：首先的确很火。昨天听《圆桌派》，窦文涛，马未都，梁文道，吴晓波这些文科生都坐在一起聊起来没完了。我也擦亮我的水晶球，扯扯我觉得未来发展的几个阶段。

第一个阶段，十年内，无人驾驶成为主流，人类开车将会成为非法行为。注意，那个时候，失业的不仅仅是司机了。餐厅，厂房车间一切地方的简单无创意的体力劳动和脑力劳动者全部失业。也就是中国会有至少80%的人失业。人类会是机器的主人，每个人活得都像个贵族，不工作，有的是钱花。所以，我觉得现还在辛辛苦苦还房贷的人都是不明智的。因为很短的时间内，人类的物质匮乏就会解除。

第二阶段，二十年内，机器学会审美，有了喜怒，可以写诗，可以写程序，做设计。人类全部失业。老年人不再孤单，因为身边会有比儿女更贴心的机器人陪护。穷苦兄弟不用担心娶不到媳妇，美女机器人到处都是。这个阶段，机器是人类的朋友，人类社会的腐败，人欺负人，各种黑暗和野蛮会基本被扫空。人类面对新一轮的伦理革命，但是爱情，友谊会取代辛劳和争斗成为所有人生活的主题。

第三阶段，三十年后，机器人在所有领域，包括道德素质，都远远超越人类。到时候，机器会把人当做小猫小狗去呵护呢，还是干脆认为人都是害虫，一下清除干净呢？不知道，但是我也不是很在乎。



## 2017.1.20：2017年有什么打算 Peter ？

@someone：2017年有什么安排呀 Peter ？

@happypeter：最重要的事情还是录视频。从2011年12月开始，我的主要工作就是录视频了，从来没变过。有朋友跟我说你这样不枯燥么？应该说没有觉得枯燥，人的性格决定的，有点数据控，喜欢不断做一件事情看着一些数字的增长。坚定方向，勇往直前，其实这个话也不是总对的。像李笑来老师，他就喜欢同时做很多事情，而且一个事一看不行就不做了，及时调整没啥不好。

职业定位上，我还是以前的老想法：帮助当初像我自己一样的，大学毕业不好找工作的年轻人。所以最近两年我也讲线下课，目标人群基本都是编程零基础的大学生。有视频配合一下教学，效果肯定好很多。

如果说到跟前两年的区别上，也是有的：第一，就是视频现在基本都配上很完整的文字稿。第二，视频总结成课程，课程总结成大的课程路线图。2016年内容创业这个词挺火，我的思路还是把 haoqicat.com 做成一个贴心服务特定人群的站点，然后上面出一两个学习路线图，作为内容产品，不断打磨。


## 2017.1.19： Peter 你为啥又对小程序亢奋了呢？

@lin：小程序通过二维码扫描传播，这个似乎只能通过线下推广，最近厂商对它的追捧明显变弱了呀？而且小程序有啥技术上的新突破么？你为啥对小程序这么追捧呢？

@happypeter：首先说这个二维码的问题。 baidu.com 搜索引擎这种方式找到网站，包括微信自己开发的小程序搜索入口，其实都还是相对中心化的找到小程序的方式，未来是个去中心化的时代，我们安装一个程序往往都是通过朋友推荐。所以二维码这种形式不是劣势，而是优势。其实 baidu.com 搜不到的问题也可以变向解决的，早晚有人开发一个”小程序的大众点评网“，这样不就能用 baidu.com 搜到了么？

厂商追捧变弱了？我自己的消息是追捧很疯狂。

小程序有技术新突破么？对比 React ，感觉小程序从技术上是一种退步，有些小创新点，但是总体上没有 React 体系更方便灵活。但是小程序开发比 React 开发更亲民，技术点的取舍方式上我也是非常喜欢的。

技术退步了，那我为啥还这么追捧呢？这几天我逢人就叨叨的理由有两点：第一，不用注册，用微信账号直接登录。你会说这个以前很多应用都是这样呀，可以用 google/facebook 登录，但是微信就是微信，不能跟其他账号同日而语。第二，一旦登录直接就可以支付了，现在年轻人还有多少微信里面没有绑定银行卡的呢，很少。上面两点我觉得就足以引发革命。





## 2017.1.18：Peter 为啥最近不用 Meteor 了呢？

@shaohailong：Peter 为啥最近不用 Meteor 了呢？

@happypeter：程序员对于技术方向的判断，就跟投资人选项目一样，是至关重要的能力，一旦选错，损失大大滴。技术是一条流淌的河流，一切都是在变化之中。

首先说说为啥当初鼓吹 Meteor 现在又放弃？我应该是国内第一批出来鼓吹 Meteor 的人，在 haoduoshipin.com 以及一些线下讲座上大力宣传 Meteor 的优势。我自己的 haoqicat.com 和 haoduoshipin.com 也都用 meteor 重写了，一直到现在 haoqicat.com 用的还是 meteor ，但是确实已经计划用 React/Express 改写了。我放弃 Meteor 有两个原因：第一个，Meteor 其实国内用的不是那么多，品牌不够大，而我是搞就业培训的，所以一定要抱粗腿，React 是一个大品牌，而 React 社区是强烈的前后端分离的这种思潮，跟 Meteor 全栈框架的思路不一致，所以我一直后端都是用 Express 。第二个原因，Meteor 真的有点发展乏力，其实社区小就是一套技术最大的短板，没人贡献第三方的库，没人贡献文档，那么用这套技术做开发效率就会明显下来了。Meteor 最早 github 上的 star 数量跟 React 差不多，但是，React 现在 github star 数量接近六万，Meteor 还是几个月前的三万多。


那么当时选择 Meteor 现在看是不是个大错误呢？算不上明智，但是不算大错误。说一点损失没有那是不可能的，但是我觉得选 Meteor 其实就是拥抱了 Nodejs ，大方向是没有错的，Meteor 也极力推崇 React ，所以这也是对的。前后端分离的确是个大趋势，Meteor 这种全栈框架生在这个前端大革命的时代，也真是算它生不逢时。放弃一个东西不证明当时选择是错误的，比如我搞 Rails 搞了五年，两年前我全面放弃 Rails ，但是即使到了今天，我依然觉得2010年的时候我选择 Rails 是我技术上做的最明智的决定之一。 Rails 的最精华的部分在 Nodejs 社区都得到了最好的继承。

最后要感慨一下：搞技术也是有风险的，咱们要把船的方向把稳。Rails 出来了，让很多写 Java/PHP 的人看起来很傻X ，React 出来了让很多写 jQuery 的人看起来很傻X，有些技术一推出，整个产业的气候风向就会发生不可逆的变化。今天我跟同事讨论，就在担心微信小程序出来了，是不是会让写 React 的人看上去很傻X ，现在还很不明朗，但是我建议你跟我一样，密切关注小程序，不要仅仅把它视作一个角落里的东西。



## 2017.1.17：React 的学习路线图应该是怎样的？


@叮叮：React 的课程 haoqicat.com 上好像没几门，React 的学习路线图应该是怎样的？

@happypeter： 整个的2016年，好奇猫上的所有课程应该都是围绕 React 来展开的，有些课程例如《跟 Peter 学 HTTP》，《 Atom 爱上 JS 》，《驾驭命令行怪兽》等等，里面没有直接用到 React ，但是也是为 React 开发者量身打造的。后台讲 Express + MongoDB 这一套，也都是为了跟 React 配合完成实际功能的。当然目前好奇猫上的课程总量也不大，总共二十几门课程。后续围绕 React 还会推出新课的。当然区别于2016年只是围绕 React 一个中心来作课程，2017年估计有很多课程是围绕微信小程序来进行的。好在二者开发技巧都是摩登 JS 开发的这一套，差别也不大。

下面说说我心目中的 React 的理想学习路线图：

- 先在学习 HTML/CSS 这个阶段，就把三大工具：Bash 命令行，Atom 编辑器，Git/Github 版本控制工具，都掌握了，这个是学 React 的基础

- 然后可以上 《 React 婴儿》在浏览器中直接使用 React （避免过早引入 Webpack 等各种工具），了解 React 的各个基本概念：State ，Props ，生命周期函数等。

- 接下来避免不了的噩梦就是 Webpack ，对初学者很不友好。所以我这几天专门录制了《 Webpack-React 环境搭建技巧》，让这个过程变得无痛。

- 这里可能有不同的思路了，但是我的想法是先不要学 Redux ，而要先上后台，学 Express ，掌握当代 Web 应用的这种前后台分离的架构。可以参考的课程就是《React-Express 极简 API》。

- 前后台都有了，就可以做实际的功能了，建议在这里停下，做几个不依赖于 Redux 的小案例，不把 React 玩熟了，上 Redux 容易晕。

- 学《塔顶上的 Redux 》课程，没有 Redux ，React 的功能也做不了多复杂。

- Redux 学完，React-Redux-Webpack 的这个体系的基础知识也就完成了。下一步就是跟着 Peter ，一起来做各种常见功能，例如注册，登录，权限控制，图片上传，文章增删改查，评论提交，数据库表关系处理等等等等，跟学其他学科一样，只学不练肯定是不成的，前期要大家自己写项目肯定很浪费时间，跟 Peter 的课程，一步步的做，相当于临摹练习了。这个目前的参考课程是《 React 手牵手》。



## 2017.1.16：Peter 后面会出数据库方面的教程吗？

@焕哥：Peter 以后会出一些数据库方面的教程吗？建议老师多讲讲服务器的知识，我作为一名前端对服务器非常不了解。

@happypeter：暂时没有打算出数据库专门的教程，因为感觉没必要。我自己从09年第一份工作开始就用 mysql 数据库，当时还看了他们几千页的那种官方手册，一直用了五六年，用 RubyOnRails 写 Web 应用的时候也主要就用 Mysql ，后来切换到 Nodejs 这边，sql 系的数据库就不怎么用了，改用文档型的 MongoDB 了，一直到现在。可以说数据库天天用，但是依然没觉察出做专门课程的需要，因为用到的东西其实都很浅的，如果你去看 haoiqcat.com 的一些案例课程，例如 http://haoqicat.com/hand-in-hand-react ，会发现关于 MongoDB 的讲解还是有的，专门讲的内容有三四小节，然后其他小节中也用到一些 MongoDB 和 JS 代码交互的技巧。所以，数据库知识，不必深入，基本的增删改查会用即可。后续如果 haoqicat.com 出专门的数据库的课程，也会是非常简单的，贴近 Nodejs 实用的简单课程。

对于前端开发者而言，后端是个神秘的世界。其实笼统来分就是两部分，一个是数据库，一个就是后端代码。除了数据库之外，如果想要成为全栈开发者，其实更大的力气应该放到如何去写服务器端代码实现 API 上。具体建议是学 express 框架，会用 curl 调试 API，懂一点后台 bash 脚本编程，会配置 Nginx 服务器。这些知识，我觉得也都是在动手中去学最好，系统的大部头的专著，不是新手应该看的。好奇猫上的所有课程，应该都是服务这个“在动手中去学”的思路的。



## 2017.1.15：目前在三线城市工作，想去一线城市发展，需要到达什么样的水平？

@ankle: 我自己接触前端一年多了，想去北上广深发展一下，目前在一个三线城市从事前端工作，流行的技术都是从互联网上学的，前端技术掌握到什么程度才适合去那里呢？

@happypeter：我自己最近十年都是在北京和三线城市之间穿梭。北京的软件产业，包括前端都是全国最发达的，比上广深都要机会更多。一线城市至少三年以上的经历，我自己觉得应该是咱们这一行人都应该尽力去获得的，确实氛围跟三线城市完全不一样。我自己最近五六年教过的学生大部分都在北京上海工作，应该说大城市工作挺好找的，初级岗位也很多。不过如果你水平太菜，到哪里都是不被重视，严重了可能会直接被边缘化，安排些杂活给你。所以我来列出一个基本的学习大纲，完成下面的内容，再去大城市应该就比较有底气了。

先说前端样式部分。最低要求，就是上手能自己写出功能性的界面，类似于 http://kf.qq.com/product/weixin.html 。了解大型项目的 CSS 组织规范，对 Sass/BEM/cssModule 这些思想中的至少一种有了解，对兼容性有基本了解，起码对 caniuse.com/autoprefixer 这些东西不陌生。最低要求是针对全栈开发者来说的，如果作为纯前端人员，那么你应该对 alistapart/css-tricks/codepen/dribbble/知乎前端话题，这些站点的大部分内容都应该感觉很亲切才行，我自己是全栈的，达不到这个境界。

前端功能实现。这部分需要了解 HTTP 的基础知识，需要灵活的用 ChromeDevtools/Curl/Postman 调试 API ，学习 vue/react/ember 这一类的框架，至少要会一种。Git/Github/StackOverflow/Google 要每天都用。这部分不管是前端开发者还是全栈开发者都应该会。

后台功能。Meteor/Rails 这样的全栈框架目前不是大趋势了。前后台分离是大方向，看看 React/Vue/微信小程序 的技术路线就很容易看出来了。所以后台我推荐的是 Nodejs，学习用 express/koa 这样的轻量级框架去动手实现 API 。会用 Mongodb/mysql 这样的数据库。当然，高手眼里是没有框架和语言的界限的，但是作为初学者，我的建议还是要瞄准一个技术栈来学。

总之，要能自己独立完成客户需求，全栈 JS 开发者工作更好找。三线城市的问题是有些技术太落后了。现在我的感受，如果你会用 React/Vue/微信小程序等这些前端方案，配合 Nodejs 做后台，独立能做成东西，你的技术栈就会是非常前卫和流行的了。特别要吹嘘一下微信小程序。Vue.js 目前的使用量还只是 React 的十分之一，在 React 这里，有 facebook/uber/airbnb/可汗学院等等一大批大项目都在用，但是用 Vue/Angular 的大项目有么？几乎没有。React 发展了这几年，社区已经非常大了。但是，注意是但是，微信小程序发布了仅仅一周，似乎就已经超越 React ，微信是一个可怕的存在。React 的影响力我感觉跟微信小程序比完全不是一个量级的，看看目前微信小程序已经商用的案例数量，github 以及各个开发社区的开源代码和文档的活跃度就知道了。

最后给我的 haoqicat.com 做一下广告，最近一年一直瞄准 React+Nodejs 来布局课程，微信小程序大量借鉴了 React/Vue 的思想，所以 haoqicat.com 上的课程学会开发微信小程序也没有问题的，最近我们也马上要上微信小程序的课程了。


## 2017.1.14：如何保持对编程的长久热忱？

@Face：编程人员如何保持对编程的热忱，避免产出逃离的想法？

@happypeter：我自己是从06年开始全职编程的，到现在十年多了，基本上是每天写代码，而且到今天对代码的热情也不减。所以我来回答这个问题还是挺合适的。也的确有很多心里话要说说。

连接人生的点。乔布斯说过，人这一辈子就是把很多个点连起来。周鸿祎说，人生没有正确的选择，我们只是努力让我们当初的选择显得更正确。我自己出生是在一个传统的农村家庭，从小喜欢读论语孟子这些东西，觉得人生就应该当个大官，出个大名，用乔布斯喜欢的话来说就是“在宇宙间画下自己的一道印”。然后，我从大学一年级开始就疯狂的喜欢上了学英语，我是班里上自习时间最长的人（我觉得我要比所有女生都长，但是没跟踪过她们，所以...），但是其他课程都不怎么学的，还挂了好几门，那你想想英语上我花了多少功夫吧。大学毕业之后，迷茫的一塌糊涂，不知道自己喜欢干什么。但是研一开始接触到了 Linux ，听了 Linus 几乎所有的演讲，其中《 Linux 起源》还有《 在 Google 讲 Git 》都听了一百遍左右。于是觉得编程才是我的人生方向，在北京工作好找，也完全对得起我的《论孟》和英文。那年就是2006年。

保持对自由的歇斯底里的热望。人是欲望的动物，脆弱而善变，我们坚持一件事情并非因为它正义，而是因为它满足了我们的私欲。我从小应该还是个乖孩子，不太喜欢攀比，现在到了30多岁，我也没有房子没有车没有一个可以回到农村老家进行吹嘘的职位。嗯，而且最重要的是我也没有孩子。我的意思是可能我跟你一样，对很多事情感觉无所谓的，但是对另外一些事情就比较挑剔。研究生的时候，我跟导师搞的很不痛快，因为他影响我学习。到了职场上我跟领导也好，合作者也好，也是说翻脸就翻脸，为啥？主要是因为学习的自由得不到保障，另外就是为啥我想下午四点出去打篮球就不行，周末景点人多，我想工作日去玩就不行。我辞去第一份工作的时候他们就跟我说，你看你还想找什么样的公司呀，咱们这个公司不但不加班，甚至也不打卡，迟到没关系。当时我的经理对我说，你就是想 do whatever you want ，他对我很不理解也很失望，觉得我不尊重公司。我的博客 happypeter.github.io 上面有一篇《狂怒者不燃尽》也说了一些类似的事。我自己脾气特别急躁，这样错过了很多可以和他人合作的机会，所以我必须要在其他的方面更努力。这么多年来我发现只要我好好写代码，就饿不着，虽然我不忠于公司，但是我尽我自己的全力去服务社会，可以给自己的良知一个安慰。写代码成了我维护自己的自由的工具了，自然也就不会厌烦了。

总结一下吧，说了很多很私人的东西，也许参考意义不大，但真的都是真心话，一些我希望跟朋友说的话。

## 2017.1.13：给大四的软件工程专业的同学的几句不中听的话

@jimmy_jude: 大四，软件工程（ Java 方向，现在立志做前端，全栈是梦想），项目经验为零， Peter 对我有何学习建议？

@happypeter: 学了四年的软件工程了，一个项目都没有做过，学校不知道是干什么吃的！我问过了，好多学校的学生都这样，毕业了，项目经验为0。

我想说的第一句话就是：没有实际动手的经验，知识基本就是垃圾。我们做编程的，学的不是知识（未来的知识也是一搜即得的），学的是 skill 也就是技能。就像英语学习一样一样的，我学了 GRE 词汇，八级英语的语法，实际听说读写能力是初一水平，那么我的整体水平就是初一。我自己在教学的时候，思路就是要用项目串起来所有的知识点，基本上参加我课程的同学，从第一天开始就是做项目，写代码，一直写到毕业。而知识点的讲解就是动手之路上的加油站，绝不多讲，刚刚够用就好。系统的学习理论知识，最终结果是系统的忘记。

第二句话：不要去考研考证抱粗腿装逼，要有服务心态。我自己就是个痴迷考研的垃圾，当初还考了两年才考上。考研考证对职业发展有没有用？有。但是就像《黑客与画家》的作者 Paul 所说，做这些事情，目的就是：Trick the System ，跟体制做捉迷藏，本质就是一种欺骗。社会是一个伟大的合作体系，人跟人直接最本质最真诚的关系是互相服务。好，你以为我这是在道德说教了，其实根本不是。首先，高科技的本质就是给个人赋权，当代社会的越来越明显的趋势就是我们不必去把自己嵌入到大组织，也一样可以很好的服务社会了。其次，也是更重要的就是，有了服务心态，学习编程你自然方向就明确了，知道什么该学什么不该学，一心去讨好考卷肯定是错误的方向，创造和创意才是正途。我的博客 https://happypeter.github.io/ 上有篇文章《为服务他人而读书》聊的也是相关内容。

总结几句：具体前端怎么学，全栈怎么学，其实很简单呀，就是跟 Google/Facebook/阿里/腾讯/饿了么/360 ... 所有这些正常的企业的最优秀的工程师去学呀，看他们的博客，到 github.com 看他们的代码，当然他们不是搞教学的，可能还是不够系统，这样你可以让 Peter 给你带带路。


## 2017.1.12：非计算机专业，如何找到第一份互联网工作？

@AlixWang 问：作为一个不是计算机专业的，现在也干的不是计算机怎么去找第一份互联网行业的工作！

@happypeter 答：首先，不是计算机专业在咱们这行里面不是问题。比尔盖茨是学法律的，扎克伯格是学心理学的，Github 的创始人 Tom 是
学物理的。说回北京，那次我们在北京中关村的车库咖啡聊天，有老手也提到说，往往干咱们这行干的最好的一批人都是跨专业的。
你也提到你现在做的不是计算机这一行，现在想要去找第一份互联网相关的工作，应该说这种情况也是非常普遍的。我
最近几年做培训比较多，班上的很多同学都是这种情况的，所以不必担心，你不是一个人在战斗。

落实到实际执行上。最老土但是其实也是最有效的方式就是，立即辞职，报个脱产的三四个月的辅导班。我自己做线下培训，
可能有王婆卖瓜之嫌疑。但是我的确认为，自学是有无数的弯路可以走的，线下班上，只要找到一个水平及格的老师，就能让
你的学习进度加快十倍。跟班上的同学一起学，然后毕业后培训机构给提供一点就业服务，大家一起去北上广找工作，
可以避免孤单和放弃。另外一个方式是利用线上资源自学，我自己是花最多时间的事情就是生产视频的，但是线上的
学习方法，更加适合老手，新手进入线上资料的海洋，没有向导，容易迷路。可以有个拜师的思路，盯着一个人学，比如
可以添加我的微信：happypeter1983 ，看看我每天朋友圈里面都关注那些知识点。一个人的思路，起码是统一的，不矛盾的。

最后说说哪些人适合干咱们这行？学校里面学四年计算机专业，帮助不大，因为学校里面讲的都是过时的东西了。我自己
班上最优秀的学生，就是那些思路清晰的学生，有些人天生思路清，善于拆解复杂问题。而有些同学就是天生不适合干这
行，胡子眉毛一把抓。
