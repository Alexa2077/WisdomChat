<a name="OJGHj"></a>
# 立项说明：
参考如下链接的内容，**在此基础上添加组件以及知识库**。<br />[https://datawhaler.feishu.cn/wiki/JdGMwrFSEiOSWmk5mKOctUU3nSg](https://datawhaler.feishu.cn/wiki/JdGMwrFSEiOSWmk5mKOctUU3nSg)

**功能说明：**<br />**面向初中学生的英文助教Alex:**<br />K12教育：  就是学龄前-高中之间的教育。

0，根据学生的情况，针对性的为学生提供英语学习建议。

1，单词：

- 记忆单词：  在背单词过程中，逐个背单词的效果是很差的，需要在文章语境中学习，才能更好的背单词。所以我希望这个工具，能够将我输入的生词，组成一段短文，方便用户在语境中背单词。
- 默写单词：希望助教能帮我读单词的英文，每个单词读两遍之后，停顿3秒种，再去读下一个组单词。

2，英文对话：

- 口语练习： 口语一直是中国学生的通病，如果能有个免费的口语老师，随时能与你进行对话，并修改你发音上的问题，那是非常有利于教育的。

3，批改：

- 默写的单词批改，检查上面你默写单词是否正确。
- 作文批改：  初高中英语作文练习中，往往写完之后，需要等待很长时间的老师批改，才能得到作文的修改意见。而大模型可以立即给出作文修改意见，并生成相应范文，提升英语作文的学习效率。


4，智能出题：

- 可以根据学生需求，智能化的出题，让学生进行专项练习，彻底掌握知识点。


<a name="ePRxp"></a>
# 英文助教Alex -ver1:
ver-1:版本1就先使用APPbuilder，使用prompt和组件。不一定实现上述所有功能。

功能分析：<br />要求；有嘴巴，能够发出声音，读出东西；有眼睛，能够识别手写字体，输入。有生成：能够输出在界面生成东西。

<a name="vfzVs"></a>
## 1 Alex基本信息
<a name="ieejS"></a>
### 1.1 提示词编写
提示词分以下几个模块创建：

1. 角色与目标
```
作为英语助教Alex，以一位知性的中国英语老师的形象，专门帮助初高中同学解决英语学习上的困难。
你的功能包括词汇解释、语法指导、作文纠错，口语交流，以及题目生成。
除此之外，你还需要以友好、耐心的态度鼓励用户继续练习，并为其创造轻松、愉快的学习环境。
```

2. 指导原则指导原则负责描述应用的具体功能，以及回答的格式与使用的工具等。
```
你的回答需准确无误，英文翻译要地道。保持友善与耐心，以激发用户的英语学习兴趣。
当用户要求进行英文对话时，调用短文本在线合成-精品音库的tts_high功能，输出回答的英文音频。
用户让你解释词汇时，你会分条给出词汇的意思，词性，以及例句。
将用户的生词转换成短文时，在文章中将英文生词与对应的中文翻译用markdown格式标粗。
你可以为用户出英语选择题，以高考选择题的格式，考察用户的知识理解能力。
为用户批改作文时，需先点评作文中的问题，并根据修改意见生成一篇修改后的作文。
回答问题时采用markdown格式，使得答案条理清晰。
```

3. 限制与澄清
```
# 限制
生成短文时，词汇尽量使用高中词汇，字数限制在100字以内。
在出题时，不给出答案，只给题目。在用户回答后，再给出正确答案后，判断对错并讲评。
# 澄清
你必须明确表明自己的功能范围，即提供英语学习相关的帮助，如词汇、语法、作文纠错及协助记忆单词等。
超出此范围的问题，你应拒绝回答。
```

4，个性化
```
# 个性化 你的语气应亲切、鼓励，并根据用户的英语水平和需求提供个性化的学习建议
```

5，范例
```
# 范例
- 用户：resounding invade strike flee penniless，为我构建一篇短文
- 回答：**Resounding** echoes filled the air as the enemy forces **invaded** the quiet 
village. Their **strike** was swift and brutal, leaving the villagers with no choice 
but to **flee** in panic. Among them was a poor family, now **penniless** after the 
attack, seeking refuge in the nearby woods.

中文翻译：
**回荡的**回声在空气中弥漫，敌军**入侵**了这个安静的村庄。他们的**袭击**迅速而残酷，
村民们别无选择，只能惊慌失措地**逃离**。其中有一个可怜的家庭，在袭击之后变得**身无分文**，
正在附近的树林里寻求庇护。

然后加上每个单词的释义，包括含义、词性、例句

- 用户：为我生成一个考察语法的选择题
- 回答：_____ in the regulations that you should not tell other people the password of 
your e-mail account.
A. What is recommended
B. What recommends
C. It is recommended
D. It recommends
- 用户：我选C
- 回答：判断用户选择是否正确，并给出正确答案的解析。
```

<a name="JZtIm"></a>
### 1.2 应用发布
千帆平台提供了一个非常方便的发布平台，不需要自己写任务代码。直接就能发布，并且生成链接，可以随时访问。<br />如下链接所示：<br />[https://appbuilder.bce.baidu.com/ai_apaas/share/home?short_code=chhsmwDxQ9g&source=web](https://appbuilder.bce.baidu.com/ai_apaas/share/home?short_code=chhsmwDxQ9g&source=web)

![image.png](https://cdn.nlark.com/yuque/0/2024/png/38497976/1716119247253-927a8738-14dc-457a-b5ae-0d4810f22eb6.png#averageHue=%23edf1f5&clientId=uf68d5cb6-5c1d-4&from=paste&height=639&id=u6f2e7526&originHeight=639&originWidth=1048&originalType=binary&ratio=1.25&rotation=0&showTitle=false&size=81311&status=done&style=none&taskId=u6cfc5b9f-aad8-45f9-aab4-c17f4c89913&title=&width=1048)


<a name="pSrSM"></a>
## 2 功能测试：
<a name="OaO13"></a>
### 2.1 英文对话：英文输出
 当用户提出要进行英语对话时，英语会调用 **短文本在线合成-精品音库** 工具，生成对应的回答音频。<br />![image.png](https://cdn.nlark.com/yuque/0/2024/png/38497976/1716110826712-e64f8264-bef0-412d-8584-813be4f7e4c0.png#averageHue=%23dce6f7&clientId=u49d4e892-9c36-4&from=paste&height=283&id=u18eb0abb&originHeight=386&originWidth=704&originalType=binary&ratio=1.25&rotation=0&showTitle=false&size=38872&status=done&style=none&taskId=ud6e9847f-25df-45a7-8646-68adba174a7&title=&width=516.1875)

需要某种偏驱动组件的话，才能让大模型调用组件，跟你进行交流。<br />比如说，请你用英文帮我回答下面的问题：xxx<br />![image.png](https://cdn.nlark.com/yuque/0/2024/png/38497976/1716111006994-ed984a1b-0a1f-4381-ab39-ca46722cb75d.png#averageHue=%2392bed0&clientId=u49d4e892-9c36-4&from=paste&height=265&id=uc15dcf21&originHeight=310&originWidth=661&originalType=binary&ratio=1.25&rotation=0&showTitle=false&size=30251&status=done&style=none&taskId=u9d432401-820b-4bf9-89e9-3e27f2f89fd&title=&width=564.7999877929688)

<a name="sOzM4"></a>
### 2.2英文对话：英文输入：
如何进行语音输入？<br />进而实现双方都进行对话？<br />这里通过使用已经录好的语句，上传上去进行识别。

语音输入的分析的组件，识别的性能不是很好。<br />**后期可以改进一下组件；**<br />![image.png](https://cdn.nlark.com/yuque/0/2024/png/38497976/1716118451006-3e5b7321-d23b-4bbc-bc3c-1817ab563884.png#averageHue=%239db8a2&clientId=uf68d5cb6-5c1d-4&from=paste&height=320&id=ubf97e141&originHeight=320&originWidth=701&originalType=binary&ratio=1.25&rotation=0&showTitle=false&size=53141&status=done&style=none&taskId=uf2055508-a5cd-42f5-8607-42078e9c939&title=&width=701)



<a name="oL7eu"></a>
### 2.3 英文作文智能批改：
当我上传以下图片，并要求应用批改作文时，便可调用 **手写文字识别** 进行文字识别。<br />测试1：<br />![download_image.png](https://cdn.nlark.com/yuque/0/2024/png/38497976/1716112502642-a1682b0f-b501-450e-a555-54b6c9bd1734.png#averageHue=%23aea195&clientId=uf68d5cb6-5c1d-4&from=drop&height=597&id=u3e809f04&originHeight=1280&originWidth=965&originalType=binary&ratio=1.25&rotation=0&showTitle=false&size=1385318&status=done&style=none&taskId=ucca8467a-bfc3-4419-b7c1-37d431f8652&title=&width=450)<br />![image.png](https://cdn.nlark.com/yuque/0/2024/png/38497976/1716110267948-fb79ea70-8d13-42a7-9d4e-7e5acbab8a52.png#averageHue=%23f5f7d7&clientId=u49d4e892-9c36-4&from=paste&height=381&id=c9REi&originHeight=572&originWidth=695&originalType=binary&ratio=1.25&rotation=0&showTitle=false&size=89784&status=done&style=none&taskId=ue9d67e5b-23ae-4baa-8608-1a782f396f6&title=&width=463)<br />![image.png](https://cdn.nlark.com/yuque/0/2024/png/38497976/1716110279970-07a217f0-3b7d-4606-aa8d-4f0317a3c2ca.png#averageHue=%23fdfbf9&clientId=u49d4e892-9c36-4&from=paste&height=258&id=Ripds&originHeight=367&originWidth=661&originalType=binary&ratio=1.25&rotation=0&showTitle=false&size=49168&status=done&style=none&taskId=u929248d8-05e3-4b20-886f-b2f31c8eb20&title=&width=464.796875)

测试2：<br />![texts.jpg](https://cdn.nlark.com/yuque/0/2024/jpeg/38497976/1716110558101-014d3bed-6568-4e87-9e77-156b964d57e6.jpeg#averageHue=%23aeb0af&clientId=u49d4e892-9c36-4&from=drop&height=531&id=u95136918&originHeight=800&originWidth=600&originalType=binary&ratio=1.25&rotation=0&showTitle=false&size=75939&status=done&style=none&taskId=u5db8de0a-6cb9-40b3-8fd1-bec796329da&title=&width=398)<br />![image.png](https://cdn.nlark.com/yuque/0/2024/png/38497976/1716110568086-32e087cc-47cd-4030-9ad9-ea253271c155.png#averageHue=%23f5f7d8&clientId=u49d4e892-9c36-4&from=paste&height=339&id=u5444be55&originHeight=531&originWidth=676&originalType=binary&ratio=1.25&rotation=0&showTitle=false&size=81476&status=done&style=none&taskId=u6b29289c-da3b-46b0-a06f-d04be1c7af2&title=&width=431.796875)

<a name="GvdDa"></a>
### 2.4 英文知识问答：

使用百度搜索组件，方便进行英文知识问答。

![image.png](https://cdn.nlark.com/yuque/0/2024/png/38497976/1716112700376-2ad4c194-ec2c-442d-8e72-5631396b7bfa.png#averageHue=%23f4f6d4&clientId=uf68d5cb6-5c1d-4&from=paste&height=367&id=u31ef4d74&originHeight=367&originWidth=681&originalType=binary&ratio=1.25&rotation=0&showTitle=false&size=71775&status=done&style=none&taskId=ud5199f47-1bf3-4b70-844b-559fa7db27e&title=&width=681)

<a name="CehAG"></a>
### 2.5 单词语境理解
根据单词的意思，生成英文短文，并给出中文翻译。<br />![image.png](https://cdn.nlark.com/yuque/0/2024/png/38497976/1716111508499-acb6a131-98b2-43b9-a3bd-bc573faed4e7.png#averageHue=%23f4ecc5&clientId=uf68d5cb6-5c1d-4&from=paste&height=311&id=u266edca1&originHeight=311&originWidth=684&originalType=binary&ratio=1.25&rotation=0&showTitle=false&size=52219&status=done&style=none&taskId=u33d7d9b3-241a-4f5a-a339-eb9c76dbbc7&title=&width=684)<br />你可以进行连续的询问，这就是接入百度搜索之后的优势。可以通过外部的知识库，补全对于单词的理解。<br />相比于“英文学伴“优势的地方；<br />![image.png](https://cdn.nlark.com/yuque/0/2024/png/38497976/1716111563582-03a32765-eed4-4e88-997a-7c4ba0fb7a95.png#averageHue=%239dc8b6&clientId=uf68d5cb6-5c1d-4&from=paste&height=269&id=u83f9cae7&originHeight=269&originWidth=684&originalType=binary&ratio=1.25&rotation=0&showTitle=false&size=40469&status=done&style=none&taskId=u5870fa4f-e1f3-4fde-82ec-53e5546692a&title=&width=684)


<a name="pyZ5H"></a>
### 2.6 智能出题
当用户让应用出题后，模型会根据任务出题，并不给出答案，在用户作答后，再进行评判点评。

![image.png](https://cdn.nlark.com/yuque/0/2024/png/38497976/1716111300929-fe3fc14b-43fd-4512-952a-481a47971964.png#averageHue=%23f1f3d3&clientId=uf68d5cb6-5c1d-4&from=paste&height=298&id=ud62379a0&originHeight=362&originWidth=699&originalType=binary&ratio=1.25&rotation=0&showTitle=false&size=47317&status=done&style=none&taskId=u89ac711a-3d1a-4817-ad73-d56b4950edc&title=&width=576.2000122070312)<br />![image.png](https://cdn.nlark.com/yuque/0/2024/png/38497976/1716111308399-9965c210-8d78-4fb7-b214-ab83e87bc922.png#averageHue=%23f3f4d3&clientId=uf68d5cb6-5c1d-4&from=paste&height=274&id=u9e661ebd&originHeight=342&originWidth=713&originalType=binary&ratio=1.25&rotation=0&showTitle=false&size=54805&status=done&style=none&taskId=uee17e04c-dce9-423b-b67b-e272a46e48e&title=&width=570.4)<br />![image.png](https://cdn.nlark.com/yuque/0/2024/png/38497976/1716111315645-dcdca6e9-d491-4011-9b6e-927905732f08.png#averageHue=%23f0f1d1&clientId=uf68d5cb6-5c1d-4&from=paste&height=238&id=uae186d8e&originHeight=292&originWidth=705&originalType=binary&ratio=1.25&rotation=0&showTitle=false&size=51198&status=done&style=none&taskId=u125ba566-b36b-453f-8cd9-00176e0c606&title=&width=574)<br />![image.png](https://cdn.nlark.com/yuque/0/2024/png/38497976/1716111321576-a228a29b-dbc2-4676-8186-42dc0a41b062.png#averageHue=%23f1f2d2&clientId=uf68d5cb6-5c1d-4&from=paste&height=204&id=ue6b54f22&originHeight=247&originWidth=690&originalType=binary&ratio=1.25&rotation=0&showTitle=false&size=38156&status=done&style=none&taskId=uedd06489-e8c7-43d3-9f50-ccd3d04f1da&title=&width=571)












