---
layout: post
title: Coding 团队如何使用 Coding 开发 Coding

---
> 原文发表于：[https://blog.coding.net/blog/how-coding-uses-coding-to-build-coding](https://blog.coding.net/blog/how-coding-uses-coding-to-build-coding)

![图片](https://dn-coding-net-production-pp.qbox.me/e1495870-c5bb-4935-b7be-778f81a92ef9.jpg) 

### Coding Anytime Anywhere

Coding 团队有 70 多人，分布在全国各地（深圳，北京，上海，成都），我们使用 Coding 作为云端办公室，以云端协作的方式管理事务，文件等，我们的日常工作（包括但不限于产品，研发，市场）都是在其上完成的。Coding 的 [全平台支持](https://coding.net/app) 让大家可以**随时随地**进行同步与协作，我们一直在践行 “Coding Anytime Anywhere”。

![](https://dn-coding-net-production-pp.qbox.me/52bd8576-1d13-474b-8fae-51dc517d00ad.jpg)


我们使用 Coding 团队功能管理团队成员和私有项目，只需要在 Coding 创建一个团队，选择迁入私有项目并添加人员，即可完成对成员，团队与项目的管理。（项目内也可以 [设置不同成员的权限](https://coding.net/help/doc/project/getting-started.html#section)）

 ![图片](https://dn-coding-net-production-pp.qbox.me/1d4ded32-844a-4a46-ae51-7111ceda7121.png) 

###  Push Everytime，Review Everything

![](https://dn-coding-net-production-pp.qbox.me/9268f573-ef55-452f-8b4d-8693586b53b6.png)

Coding 的工作流（从需求到产品原型到开发）都是在项目内进行的：我们使用讨论和任务功能管理需求，使用文件功能管理产品原型，使用代码功能进行开发，这也便于每个人随时 Follow 或 Review 任务，文件或代码。

![图片](https://dn-coding-net-production-pp.qbox.me/a71f4a41-7e9f-4ff2-b087-1a4c280be3ce.png) 

#### 需求

我们使用 Coding 的 [公开项目讨论功能](https://coding.net/u/coding/p/Coding-Feedback/topic) 收集用户反馈，提炼核心需求并定期 Review 进行取舍。

> 为什么要 Review 产品需求？
软件缺陷并不只是在开发阶段才产生，需求和设计阶段同样可能会产生缺陷。

 ![图片](https://dn-coding-net-production-pp.qbox.me/df1d1dba-bd8e-444c-b340-9f3920fe9bf3.png) 

#### 产品

当产品研究决定我们要实现某功能时，我们会以任务形式发布该需求，然后进行技术评审（如果是重大新功能还需要进行设计评审），评审完成且结果为肯定时我们会继续细化（修改）该任务，进行产品设计及排期。

 ![图片](https://dn-coding-net-production-pp.qbox.me/8d0bc6d5-bffc-4256-b6ec-d4db07602fb5.png) 

在产品设计过程中，我们使用 Coding 的文件管理功能进行对产品原型的管理和版本管理。

 ![图片](https://dn-coding-net-production-pp.qbox.me/7a8cf1fa-2bfc-44e9-ac8b-63108020915c.png) 

#### 开发

Coding 的开发方式，更像是一个大型的开源项目协作。当需求及产品原型以任务形式确定后，开发人员就开始基于自己的功能分支进行开发，其后的代码评审是也是通过项目内提交 MR （[合并请求](https://coding.net/help/doc/git/git-branch.html#section-8)）进行的。

 ![图片](https://dn-coding-net-production-pp.qbox.me/03468d9b-ea68-4a50-96b3-4b28ad0c6964.png) 

我们使用了 Feature Branch Workflow，即团队成员共用一个私有项目仓库进行管理协作，开发者在各自的 feature-branch 中进行开发，开发完成后通过提交 Merge Request 进行代码评审，通过代码评审后 merge 进入 master 分支（ master 分支是可部署到 staging/生产环境的分支）。

 ![图片](https://dn-coding-net-production-pp.qbox.me/2c8e66c8-c781-4c49-ae8c-9fa6beb9b132.png) 

> 工作流（Workflow），是对工作流程及其各操作步骤之间业务规则的抽象、概括描述。合理选择并使用一套工作流可以让技术团队开发更高效，更简单！

>Workflow 没有银弹 ，如果你的：
- 生产环境有多个版本，需要持续支持旧版本的软件服务如操作系统，自定义应用程序等，可使用 Gitflow
- 生产环境只有一个版本，如网站，网络服务等，可使用 Feature Branch Workflow
- 生产环境只有一个版本但软件很复杂，需要 CI/CD 后才能进入生产环境的如 Gmail，Twitter 等，可使用 Gitlab-flow


#### 测试与上线

当开发人员  push 代码后会触发 [Webhook](https://open.coding.net/webhook.html)，我们的 Jenkins 会自动编译并测试该 commit。

> 你的部署工具应该支持你部署分支是很重要的。一旦你确认你的性能没有波动，没有稳定性问题，功能可用性在预期内，你就可以 merge 它了。这么做的原因不是为了确保事情可行，而是防止事情不可行。当其出错时，你的解决方案应该是单调，直接且无压力的：重新部署 master 分支即可。就是这样，你回到了“没问题”的状态。—— [《如何部署软件》](https://blog.coding.net/blog/deploying-software)

 ![图片](https://dn-coding-net-production-pp.qbox.me/bdb0e020-87c3-4e70-b395-8cf011324493.png) 

当测试通过时，我们会更新代码到 Staging 环境，更新好后由测试人员进行相关测试。Staging 环境测试没问题后，我们会以 Feature Flags （内部测试新功能）的形式发布其到生产环境，通知相关的产品或设计人员开启 Feature Flags 进行内部 Review，如果存在问题或缺陷，我们会新建一个任务进行修复，确保功能及设计细节的正确性。

 ![图片](https://dn-coding-net-production-pp.qbox.me/39bc32d8-cac5-4ac4-a91d-d7b01f373da0.png) 

如果经测试新功能确认没问题后，我们会开放该 Feature Flags，将该功能开放给全体用户。


### 结语

Coding 始终认为开发工具应该足够简单，开发人员的生成力应该被解放出来，我们使用 Coding 这个开发工具进行开发，旨在不断优化提升 Coding 的体验，让开发更简单。当然，如果你有任何需求或建议，请不要忘了 [提交给我们](https://coding.net/feedback) ；）

 ![图片](https://dn-coding-net-production-pp.qbox.me/ac25aa87-b312-4818-a696-c31c6b5ddb8e.png)

**Happy Coding!**

> 感谢 [Summer](https://coding.net/u/zengsha)，[skywalker_z](https://coding.net/u/rexskz) Review 了本文并提出修改意见，感谢 [tankxu](https://coding.net/u/tankxu) 设计的图片（How Coding uses Coding to build Coding）