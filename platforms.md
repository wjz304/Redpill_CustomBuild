> 摘自 https://xpenology.com/forum/topic/61634-dsm-7x-loaders-and-platforms/


7.x Loaders and Platforms as of 06-June-2022



选项 | 1a | 1b | 2a | 2b | 2c | 3a | 3b  
-|-|-|-|-|-|-|-   
DSM 型号 | DS918+ | DS3622xs+ | DS920+ | DS1621+ | DS3617xs | DVA3221 | DS3615xs  
Architecture | apollolake | broadwellnk | geminilake | v1000 | broadwell | denverton | bromolow  
DSM 版本 | 7.0.1-7.1.0-42661 | 7.0.1-7.1.0-42661 | 7.0.1-7.1.0-42661 | 7.0.1-7.1.0-42661 | 7.0.1-7.1.0-42661 | 7.0.1-7.1.0-42661 | 7.0.1-7.1.0-42661  
驱动器映射 | sataportmap/diskidxmap | sataportmap/diskidxmap | device tree | device tree | sataportmap/diskidxmap | sataportmap/diskidxmap | ataportmap/diskidxmap  
QuickSync 转码 | Yes | No | Yes | No | No | No | No  
NVMe 缓存支持 | Yes | Yes | Yes | Yes | Yes (as of 7.0) | Yes | No  
RAIDF1 支持 | No | Yes | No | No | Yes | No | Yes  
最低 CPU 支持 | Haswell * | any x86-64 | Haswell * | any x86-64 | any x86-64 | Haswell * | any x86-64  
最大 CPU 线程 | 8 | 24 | 8 | 16 | 24 (as of 7.0) | 16 | 16  
注意事项 | 适合大多数用户 | 适合大型环境安装 | 需要了解dts | AMD Ryzen, 需要了解dts | 过时(建议使用DS3622xs+)  | AI/深度学习 nVIDIA GPU | 过时(建议使用DS3622xs+)  


* \* 需要 FMA3 指令支持。所有 Haswell Core 处理器(4代)或更高版本都支持它; Pentiums/Celerons(J系列的 CPUs 除外) 很少支持. Piledriver 是与 Intel Haswell 相当的最低 AMD CPU 架构.


建议:  
## 1a. 默认安装 DS918+ 7.1.0  
优势：硬件转码、NVMe 缓存支持、从 6.2.x 直接迁移平台  
先决条件：英特尔 Haswell（又名第 4 代）或更新的 CPU 架构（或 AMD 等效产品）  
兼容性故障排除选项：虚拟化、DS3622xs+、DS1621+（适用于 AMD 系统）  

## 1b. 大型系统安装 DS3622xs+ 7.1.0  
优点：支持 RAIDF1、多达 24 个 CPU 线程、增强的 SAS 支持、NVMe 缓存支持  
兼容性故障排除选项：虚拟化、DS1621+（适用于 AMD 系统）  

## 2a. 最新平台安装 DS920+ 7.1.0  
优点：支持 NVMe 高速缓存，如果需要最新版本的 DS9xx+ 平台  
先决条件：英特尔 Haswell（又名第 4 代）或更新的 CPU 架构（或 AMD 等效产品）  
兼容性故障排除选项：虚拟化、DS3622xs+、DS1621+（适用于 AMD 系统）  
注：此型号需要设备树配置，但尚未 100% 正常工作  
与 DS918+ 相比没有额外的功能特性  

## 2b. AMD 平台安装 DS1621+ 7.1.0  
优点：NVMe缓存支持，使用AMD芯片组和Ryzen CPU的AMD特定构建（似乎在英特尔上运行良好）  
注：此型号需要设备树配置，但尚未 100% 正常工作  
兼容性故障排除选项：虚拟化  
与其他平台相比没有额外的功能特性  

## 2c. 备用安装 DS3617xs 7.1.0  
优势：RAIDF1 支持、增强的 SAS 支持、从 6.2.x 直接迁移平台  
注：技术上已过时，由DS3622xs+取代  
兼容性故障排除选项：虚拟化、DS1621+（适用于 AMD 系统）  

## 3a. 深度学习/人工智能平台安装 DVA3221 7.1.0  
优点：原生 nVIDIA GPU 支持（用于 AI，没有明显的转码功能），NVME 缓存支持  
先决条件：英特尔 Haswell（又名第 4 代）或更新的 CPU 架构（或 AMD 等效产品）  
兼容性故障排除选项：虚拟化  

## 3b. 传统安装 DS3615xs 7.1.0  
优势：RAIDF1 支持、增强的 SAS 支持、从 6.2.x 直接迁移平台  
注：技术上已过时，由DS3622xs+取代  
注意：已知此平台在负载下会出现内核崩溃 
注：7.1.0 是 DS3615xs 的最后一个 DSM 版本，群晖科技不会提供进一步更新  
兼容性故障排除选项：虚拟化、DS1621+（适用于 AMD 系统）  