---
layout: post
title:  "動手實作學習RISCV RV32I架構文章系列"
date:   2018-01-10 23:00:00 +0800
categories: blog tc-post
---

嗨, 您好. 感謝您對RISCV架構感興趣而來閱讀相關內容.

此文章是整理去年11月到今年1月間製作RISCV基礎32位元架構(RV32I)設計專案[(learn-rv32i-asap)](https://github.com/watz0n/learn-rv32i-asap)的相關心得與方法介紹, 內容參考自[RISCV Sodor Project](https://github.com/librecores/riscv-sodor). 始於應用加州柏克萊大學新的硬體描述語言, Chisel3, 第三代架構在Scala上的新語言進行RV32I核心設計. 並銜接開源數位模擬軟體Verilator來進行功能驗證, 最後建立RISCV Front-End Server(FESVR)與RISCV除錯模組的通道, 將測試用二進位執行檔案送入RISCV模擬器來檢驗實際運作功能. 目前在開始編寫文件階段, 會逐步更新當時設計的相關內容.

目前規劃會介紹下列內容:
1. 何為硬體描述語言Chisel3? 如何應用此語言用於建立電路行為模型?
2. 何為RISCV基礎32位元架構(RV32I)? 如何應用Chisel3來進行設計?
3. 何為RISCV控制與狀態站存器(CSR)? 如何加入RV32I核心來擴增功能?
4. 何為RISCV除錯模組(DM)? 如何連接到RV32I核心來進行操作?
5. 何為RISCV FESVR? 如何用FESVR將二進位執行檔案經由除錯傳送模組(DTM)來大量檢驗功能?

預計會更新文章連結在下方, 直到相關內容更新完成為止.

---

### 1. 加州柏克萊大學硬體描述語言, Chisel3相關介紹

TBD

---

EX. 相關學習資料  
===

以下為實作此設計時有用到的相關資料, 如果覺得缺乏相關知識請優先閱讀.

大學課程 (線上資料)
===
* 經由實作GCD Module來學習Chisel3
    * [UC Riverside EECS168](https://github.com/sheldonucr/ucr-eecs168-lab/tree/master/lab4) : 使用這簡單的GCD行為模型.
    * [MIT 6.884](http://csg.csail.mit.edu/6.884/handouts.html) : 應該是大部分美國大學教學GCD模組的來源, 學習其可合成(synthesizable)設計方法.
    * [Berkeley CS250 FA09](https://inst.eecs.berkeley.edu/~cs250/fa09/) : 參考使用其模組輸入/輸出介面.
* 實作RV32I核心
    * [Berkeley CS61C SP16](http://inst.eecs.berkeley.edu/~cs61c/sp16/) : 舊RISC架構的入門課程, 並為RISCV教學課程CS152的前置課程. 今年新開的[CS61C FA17](http://inst.eecs.berkeley.edu/~cs61c/fa17/)使用新版的RISCV教科書作為授課內容.
    * [Berkeley CS150 FA13](http://www-inst.eecs.berkeley.edu/~cs150/fa13/) : 
    此課程的介面設計有介紹ValidIO/DecoupledIO相關內容.
    * [Berkeley CS152 FA16](http://www-inst.eecs.berkeley.edu/~cs152/fa16/): RISCV開始被用於授課的地方, 建議實作前先多閱讀幾次課程講義, 對於時作概念非常實用.

線上課程
===
* [MITx 6.004x 系列](https://www.edx.org/course/computation-structures-part-1-digital-mitx-6-004-1x-0) : 讓我能理解數位電路世界的課程, 並藉由以邏輯閘(Logic-Gate)設計MIT規劃的Beta處理器經驗來調整RV32I核心設計內容. 如果你沒有edX.org帳號, 這邊也有[官方網站](http://computationstructures.org/)可以遊覽內容.
* [MITx 6.005x 系列](https://www.edx.org/course/software-construction-java-mitx-6-005-1x) : 讓我了解Java並能應用的課程. 應用課程中錯誤處理機制(Exception)經驗來處理Chisel回報錯誤的問題.

書籍
---
* [The RISC-V Reader: An Open Architecture Atlas](http://riscvbook.com/) : 非常棒的書籍, 尤其對Control and Status Register (CSR) 相關介紹目前最具體的書籍.
* [Programming in Scala, First Edition](https://www.artima.com/pins1ed/) : 非常完整的Scala教學書籍, 建議在實作Chisel3前閱讀過.

維基
---
* [Chisel3 Official Wiki](https://github.com/freechipsproject/chisel3/wiki) : 
Chisel3官方Wiki, 有大量參考設計資源.
* [Chisel Learning Journey](https://github.com/librecores/riscv-sodor/wiki/Chisel-Learning-Journey) : 在2017年12月後的更新, 是個超棒的資料庫, 尤其是其 [Overview page](https://github.com/librecores/riscv-sodor/wiki/overview) 有很重要的Debug Module非0.13版官方指令如 0x44(重置RISCV核心).

實作專案
---
* [GitHub learn-chisel3-gcd](https://github.com/watz0n/learn-chisel3-gcd) : Chisel3學習經驗
* [GitHub learn-rv32i-unittest-alu](https://github.com/watz0n/learn-rv32i-unittest-alu) : 最開始製作RV32I核心的一步, 實作ALU相關的Data-Path.
* [GitHub learn-rv32i-asap](https://github.com/watz0n/learn-rv32i-asap) : 目前初步完成的RV32I核心模擬器.
