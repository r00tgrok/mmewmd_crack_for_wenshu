# 文书网反反爬虫SDK
# TIP：由于近期有众多开发者将项目应用于某网站的爬虫，导致其现在无法很难像之前一样正常访问，在这里我呼吁各位请不要做违法的事情，如果用于采集数据，请保证数据用于非商业用途，否则后果自负！！另外如果您真的用于爬虫，希望尽量放慢速度，让网站正常访问，让想学习js“搞基”特性的朋友有机会进行调试学习。多说一句，大家都是程序员，程序员何必为难程序员，大家细水长流，别把某网站的程序员惹急了谢谢大家，再次感谢各位捧场的朋友，感谢某数的反扒工程师让我们认识了那么多有趣的加密方案，也感谢某书网提供的学习平台。大家新年快乐！！！另外提醒一下，无论是在哪个系统环境下调用，请安装nodejs。
## 前言
一月份的时候中国裁判文书网更新了据说是瑞数安全的js混淆动态加密。 <br>
特征1：params:MmEwMd <br>
特征2：html:9DhefwqGPrzGxEp9hPaoag <br>
特征3：cookies：FSSBBIl1UgzbN7N80T

## 项目
本项目为学习Js加密和向反爬虫工程师前辈们学习而立，请勿用于违法用途，用于违法用途产生的后果与本人无关，本版本仅供学习参考所用，所有下载者应于24小时内学习完毕后删除。
由于本次项目需求的朋友来自使用各个开发语言，本次sdk将会js的方式提供，各开发者可以根据自己开发语言考虑采用v8引擎执行或语言自带的执行js的函数或者是第三方包。

## 调用思路
[请严格按照此思路调用，否则会出现大量remindkey或者202]

###定义:
#### 完整生命周期
第一步:
必须至少进行一次二次跳转:

①第一次访问List页应当cookies中不含有F80系列cookies，此时必定202，并返回F80S和假F80T, 获得meta头

②第二次访问List页应当带上第一次访问返回的F80S和用第一次返回的假F80T生成的真F80T，此时会返回vjkl5， 获得meta头

第二步:
此时我们应当保存上一步最后请求时的真F80T，还有①中的F80S, vjkl5, ②中的meta头。
之后的每一次访问ListContent页面，都需要使用上一次访问时（在第一次访问ListContent的时候，用的是②中的真F80T）的真F80T去生成新的真F80T，且每次生成的F80T仅可使用一次后作废，作废后用于生成下一次新的真F80T。

#### 爬虫生命周期理论
当遇到了任何一个接口返回码为202时，意味着一次上述的完整证明周期结束。需要重新按照上面的生命周期运行。
此处包含，访问时出现的202或者是更换了代理IP。



## 更新tip

### 2019.2.11-2
修复windows下兼容性问题，现在再也不需要nodejs啦
阿布云也可能没啥用了，所以改成通用的代理测试版本

### 2019.2.11-2
测试阿布云专业版可以获取到数据，做了一个加上代理IP的版本给大家参考,自行处理返回值为空和因代理IP其他报错问题。
注意，一定要是专业版的阿布云，别买错了！！


### 2019.2.11
Python调用示例添加解密docid和获取详情页的方法。

<b>重要提示：目前因为用本项目做采集的开发者较多，采集量非常大，导致瑞数现在开始疯狂地封IP。基本上百度上能搜到的那几家大代理商获取数据相对慢点,大户请各位自行开动脑经或者找关系找一些非公开销售的代理IP。</b>
目前本项目依旧正常可使用，请严格按照demo的调用方式调用。

大量出现202基本肯定是封IP，400可以进行5-10次的重试。按照demo的调用流程相对比较省IP，我指的是获取到list的后直接去获取内容页数据，过往大家一般是存docid到队列。这里可以改成把获取到的未处理的数据放到队列，比较省IP。

附加2019.2.11调用结果log，可自行查看

### 2019.1.21
修复了大量可能会出现remind key和202的问题。

合并了来自@jjk13593527343开发者制作的go语言调用sdk，go开发者请前往gland_mmewmd文件夹调用

### 2019.1.20
在连续5天的奋战下，我们sdk最终版终于完成！本项目以jssdk为核心，本次发布python调用实例，敬请参考。
将在未来1-2天内发布java，go，c#的实例版本，欢迎大家star和加入我们这个有爱的数据矿工(下🈶群号)群体。
一测试：商标网已通杀可通过本sdk访问。

python版：guid请自行找算法生成，否则会remind key！！（最新版已解决）

本次开发全程直播，将由"时光机"和老高两位志愿开发者将视频剪辑后发布，具体视频地址敬请期待（因某些原因暂不公开）。
虎牙直播间:17593443欢迎订阅

[一个97少年的战斗史]

### 2019.1.17
这个版本加密里面工程师下的毒太多了，现在上传的是已经确定加密过程，但由于部分加密参数获取的生成方式依旧不是很全面，所以暂时无法通过瑞数的审核，带生成的参数访问页面会400错误。
不过现在可以肯定的是目前这个版本是整个MmEwMd的主要生成方式，待我整理思路把不确定的参数生成方式全部弄清楚，会给大家继续献上完整SDK。下次更新时间预计为2019.1.19之前。

请clone代码后，清空浏览器缓存打开文书网，把当前的cookies中的FSSBBIl1UgzbN7N80T参数值填写到python代码对应位置直接运行生成的就是MmEwMd参数。
关于MmEwMd：已经通过比对，确认生成的长度和规则是一致的。

## 快乐的爬虫群
**QQ119794042**



### 鼓励
如果我的项目帮助到了你，可否通过打赏鼓励一下作者


<img src="https://github.com/sml2h3/mmewmd_crack_for_wenshu/blob/master/1548066223468.jpg" width="366" hegiht="570" style="display: inline-block"/>
<img src="https://github.com/sml2h3/mmewmd_crack_for_wenshu/blob/master/mm_facetoface_collect_qrcode_1548066239153.png" width="366" hegiht="570" style="display: inline-block"/>
