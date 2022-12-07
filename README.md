# Redpill_CustomBuild
[![](https://img.shields.io/github/issues-search?label=%E5%AE%9A%E5%88%B6%E6%AC%A1%E6%95%B0&query=repo%3Awjz304%2FRedpill_CustomBuild%20label%3Acustom)](https://github.com/wjz304/Redpill_CustomBuild/issues?q=label%3Acustom)
[![](https://img.shields.io/github/issues-search?label=%E6%AF%8F%E6%97%A5%E6%9E%84%E5%BB%BA&query=repo%3Awjz304%2FRedpill_CustomBuild%20label%3Aschedule)](https://github.com/wjz304/Redpill_CustomBuild/issues?q=label%3Aschedule)  

## 介绍  
[Redpill_CustomBuild](https://github.com/wjz304/Redpill_CustomBuild)  
[Redpill_CustomBuild_v1](https://github.com/wjz304/Redpill_CustomBuild_v1)(old)  
一个自定义配置及驱动并通过 Github Action 编译 DSM redpill 引导的平台.  
本库并没有实际的技术创新, 仅做了一个参数适配, 使一些定制更简单, 并把过程搬到线上, 依赖微软强大的服务器使其快速得到想要的引导文件.  
高度依赖以下大佬的项目, 请给以下各位大佬点赞.
>源码仓库： [@RedPill-TTG](https://github.com/RedPill-TTG/redpill-load)  
>编译来源： [@pocopico](https://github.com/pocopico/redpill-load) [@jumkey](https://github.com/jumkey/redpill-load) [@PeterSuh-Q3](https://github.com/PeterSuh-Q3/redpill-load) [@fbelavenuto](https://github.com/fbelavenuto/arpl)  
>驱动来源： [@pocopico](https://github.com/pocopico/rp-ext) [@jim3ma](https://github.com/jim3ma/synology-igc) [@fbelavenuto](https://github.com/fbelavenuto/r8125)  

在此, 再次, 声明!!!  
本人只是按照通用编译流程整合各位大佬的redpill-load 进行编译. 我只是解决编译的问题, 任何引导内部问题我都解决不了(当然知道的问题肯定会协助大家解决).  
说通俗点, 我只是相当于一个物流, 你要哪家(大佬)的货(引导)我就给你配送哪家(大佬)的货(引导).


> 😎 为什么用 GitHub Action？  
> 托管于 GitHub 服务器, 只要 GitHub 不宕机, 它就不受影响(Private 项目每月有 2000 次的限制, Public 项目无限制).

## 链接
***如果没有魔法，请参考 https://github.com/wjz304/hosts 设置hosts***  
***请使用 Chromium 内核浏览器 (Chrome / Edge / 360极速 ...)***  
[【👉快速创建】](https://wjz304.github.io/Redpill_CustomBuild/Issues.html)  
[【👉快速创建】(dev)](https://wjz304.github.io/Redpill_CustomBuild/Issues.html?dev=1)  
`普通模式默认使用pocopico的驱动库, dev模式默认使用我fork的驱动库(如果报 Checksum 错, 请尝试使用(dev)模式), `  
`并发较多时, 有概率出现curl错误或者 未触发编译的情况, 过几分钟再试...`  
`如果你看不懂, 或者其他疑难杂症, 请不要浪费时间. 尝试使用arpl构建. https://github.com/fbelavenuto/arpl`

## 使用  
在本项目 Issues 中创建问题(符合下述规范), 按需填写即可发起定制构建[【👉图文说明】](https://github.com/wjz304/Redpill_CustomBuild/blob/main/guide/Issues.md) [【👉注意事项】](https://github.com/wjz304/Redpill_CustomBuild/blob/main/tips.md).  

### Issue title:
标题请以 custom 开头(不区分大小写), 且不要包含'(单引号),"(双引号) 等转义字符.
### Issue body:
内容 以json格式编写(切记符号为英文符号, [【👉JSON检测】](https://json-online.com/check/))

参数             | 必选 |     默认值     | 说明  
-----------------|------|----------------|---------  
repository       | √    |-               | 请选择编译依赖的基础库. "pocopico_develop", "pocopico_jun", "jumkey_develop", "PeterSuh-Q3_master"  
platform         | √    |-               | 请选择你需要编译的型号. (具体包含型号以基础库支持为准)  
version          | √    |-               | 请选择你需要编译的版本. (具体包含版本以基础库支持为准)  
lkm              | ×    |-               | 如不了解请保持默认, 请选择 LKM 版本.(目前具体有何区别不详, 如无必要选默认的 redpill).  
config           | ×    |-               | 如不了解请保持默认, 设置默认 user_config.json <sup>[①]()</sup>
maxdisks         | ×    |-               | 如不了解请保持默认, 请输入最大硬盘数 maxdisks. 默认: 无, 范围: 1~32  
maxlanport       | ×    |7               | 如不了解请保持默认, 请输入最大网卡索引 maxlanport. 默认: 7, 范围: 0~31  
internalportcfg  | ×    |"0xffff"        | 如不了解请保持默认, 请输入sata接口配置 internalportcfg(十六进制数). <sup>[④]()</sup> 默认: 0xffff  
esataportcfg     | ×    |-               | 如不了解请保持默认, 请输入esata接口配置 esataportcfg(十六进制数). <sup>[④]()</sup> 默认: 无  
usbportcfg       | ×    |-               | 如不了解请保持默认, 请输入usb接口配置 usbportcfg(十六进制数). <sup>[④]()</sup> 默认: 无  
~sn~             | ×    |-               | ~序列号. 默认根据型号随机生成.~ <sup>[②]()</sup>  
~mac~            | ×    |-               | ~MAC地址. 多个请以 "," 间隔. 默认根据型号随机生成.~ <sup>[②]()</sup>  
netif_num        | ×    |2               | 请输入网卡数量 netif_num. 默认: 2, 范围: 1~8  
vid              | ×    |"0x46f4"        | 请输入USB设备供应商识别码(Vender ID). 默认: 0x46f4  
pid              | ×    |"0x0001"        | 请输入USB设备产品识别码(Product ID). 默认: 0x0001  
diskidxmap       | ×    |-               | 请输入SATA控制器盘序 DiskIdxMap. <sup>[④]()</sup> DS920+, DS923+, DS1520+, DS1621+, DS2422+, DVA1622 不需要填写. 默认: 无  
sataportmap      | ×    |-               | 请输入SATA控制器盘数 SataPortMap. <sup>[④]()</sup> DS920+, DS923+, DS1520+, DS1621+, DS2422+, DVA1622 不需要填写. 默认: 无  
sasidxmap        | ×    |-               | 请输入SAS控制器盘数 SasIdxMap. <sup>[④]()</sup> DS920+, DS923+, DS1520+, DS1621+, DS2422+, DVA1622 不需要填写. 默认: 无  
dtb              | ×    |-               | 请输入dtb 文件的下载链接(支持的文件类型: .dts,.dtb,.tar.gz,.zip), 仅 DS920+, DS923+, DS1520+, DS1621+, DS2422+, DVA1622 需要填写, 其他型号请勿填写. [#47](https://github.com/wjz304/Redpill_CustomBuild/issues/47)  
ext              | ×    |-               | 请输入需要集成的扩展, 多个请以 "," 间隔. 支持名字（pocopico库）或者链接，名字参考[exts.json](./exts.json). eg: "r8125, tg3" 
\-               | ×    |-               | 高级自定义 <sup>[③]()</sup>  

```
①: 格式 json, key会更新到默认的user_config.json中, 因此请谨慎编写.
  - 比如 想修改 maxlanport, 需要填写完整的 synoinfo 属性, 当仅填写 {"synoinfo": {"maxlanport": "8"}} 时, 将更新 synoinfo 为只有 maxlanport, 原有 internalportcfg 将会丢失.
②: 由于SN/MAC发生盗用情况, 不再接受SN/MAC的定制, 请勿再填写.
③: body 中可直接插入shell脚本："由于权限太高, 防止有些人执行非法操作, 仅仓库作者可操作, 请联系该仓库管理员或者fork到自己名下操作."   
  - 在 body 中 以 ```xxx``` 包裹自定义的 shell 命令, 将在 build 前运行. 参考[#3](https://github.com/wjz304/Redpill_CustomBuild/issues/3) 
④：详细信息请查看：https://github.com/wjz304/Redpill_CustomBuild/issues/1252#issuecomment-1242677916
```

## 说明
0. __感谢 [hoping](https://github.com/htmambo) 大佬制作的 WEB 界面.__  
1. 构建成功 Issues 会自动 closed.  
2. 构建失败 后请调整参数重新创建Issues发起重新构建, 或者修改body后 Close Issue + Reopen 重新触发.（触发编译：open, reopen）. 
3. 再次构建, 直接 reopen 会再次触发构建. 
4. 每日构建, 打上'schedule' [【👉标签说明】](https://github.com/wjz304/Redpill_CustomBuild/blob/main/guide/Issues.md#issues-%E6%AF%8F%E6%97%A5%E5%BE%AA%E7%8E%AF%E6%9E%84%E5%BB%BA%E6%95%99%E7%A8%8B)标签 将会每日构建(通过Reopen的方式, 因此如果构建失败Issues没有Closed 将终止).  
5. 驱动的选择请参考[【👉驱动列表】](./drivers.md).     
6. 根据github官方说明所有的编译结果保留90天，周知.
7. 如果没有魔法, 参考 https://github.com/wjz304/hosts 设置 hosts.
8. [【👉问题反馈】](https://github.com/wjz304/Redpill_CustomBuild/issues/807)  交流群 QQ群: [21609194](https://qm.qq.com/cgi-bin/qm/qr?k=8AU8VJ82OR2HB_77g3vsjGKA-rm-p67B&jump_from=webapi)  TG: [https://t.me/Redpill_CustomBuild](https://t.me/Redpill_CustomBuild)  
 `(PS: 在Issues上评论我可能看不到, 邮件太多了, 如长时间未回复请私信.)`  
9. fork 本项目 Issues 和 Action 使用没有问题的.  
  但是快速创建的WEB页面由于 涉及 guthub 的 pages, 且含有CDN加速, 存在一些硬编码, 如要使用, 需要开通pages后方可使用.  
10. 在Issues下评论 "transfer" 附件转快传 🚲->🏍. (请勿重复发, 转换操作时间 ≈ 该Issue编译成功次数 X 3分钟).
11. 在Issues下评论 "delete builds" 即可删该Issues的所有历史编译记录.
12. Web页 Title 后面的红色标签是可以点击的哦!(***PS：只有读到这里的人才会知道.***)  

## 举例
* 普通参数示例:
  - {"repository":"pocopico_develop", "platform":"DS3622xs+", "version":"7.0.1-42218", "lkm":"redpill", "ext":"r8125, tg3"}  
  - {"repository": "jumkey_develop", "platform":"DS3622xs+", "version":"7.0.1-42218", "lkm":"redpill", "ext":"r8125, tg3"}  
  - {"repository":"pocopico_develop", "platform":"DS3622xs+", "version":"7.0.1-42218", "lkm":"redpill", "vid":"0x0525", "pid":"0xa4a5"}  
  - {"repository":"pocopico_develop", "platform":"DS3622xs+", "version":"7.0.1-42218", "lkm":"redpill", "diskidxmap":"00", "sataportmap":"6", "ext":"r8125"}  
  - {"repository":"pocopico_develop", "platform":"DS3622xs+", "version":"7.0.1-42218", "lkm":"redpill", "maxdisks":"16", "maxlanport":"7", "ext":"r8125"}  
  - {  
      "repository":"pocopico_develop",  
      "platform":"DS3622xs+",  
      "version":"7.0.1-42218",  
      "lkm":"redpill",  
      "netif_num":"3",  
      "ext":"r8125, r8168, e1000e, igb, vmxnet3, ixgbe"  
    }  
* dtb参数示例:  
  - {  
      "repository":"pocopico_develop",  
      "platform":"DS920+",  
      "version":"7.0.1-42218",  
      "lkm":"redpill",  
      "dtb": "https://github.com/wjz304/Redpill_CustomBuildfiles/9235785/ds920p.zip",  
      "ext":"r8125"  
    }  
* ext参数链接示例:  
  - {  
      "repository":"pocopico_develop",  
      "platform":"DS3622xs+",  
      "version":"7.1.1-42962",  
      "lkm":"redpill",  
      "ext":"r8125, e1000, e1000e, vmxnet3, https://raw.githubusercontent.com/wjz304/rp-ext/main/rtl8150/rpext-index.json"  
    }
* config参数示例:  
  - {  
      "repository":"pocopico_develop",  
      "platform":"DS3622xs+",  
      "version":"7.0.1-42218",  
      "lkm":"redpill",  
      "config":{"ramdisk_copy": {}},  
      "ext":"r8125, e1000, e1000e, vmxnet3"  
    }  
* 高级自定义示例:
  - {"repository":"pocopico_develop", "platform":"DS3622xs+", "version":"7.0.1-42218", "lkm":"redpill", "ext":"r8125,e1000e,vmxnet3"}  
    \`\`\`  
    echo "${platform}"  
    \`\`\`  
    
</br>
<details><summary>🍻打赏一下</summary>  
<div><img src="https://raw.githubusercontent.com/wjz304/wjz304/master/my/20220908134226.jpg" width="500"></div>  
</details>  
</br>

## 鸣谢
https://github.com/RedPill-TTG/redpill-load  
https://github.com/jumkey/redpill-load  
https://github.com/pocopico/redpill-load  
https://github.com/PeterSuh-Q3/redpill-load  
https://github.com/Online24Hours/Redpill_Build  

