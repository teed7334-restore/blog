---
layout: post
title:  "VSCode透過SonarQube即時驗証程式碼"
date:   2021-02-25 00:00:00
categories: 軟體設定
tags: 軟體設定
excerpt: VSCode透過SonarQube即時驗証程式碼
mathjax: true
---

![/blog/images/202102252220.jpg](/blog/images/202102252220.jpg)

在 [開發自動化](/blog/2020/05/12/開發自動化/) 這篇我有提過一次，如何透過SonarQube來幫我們檢查程式碼有那邊可能會有問題需要修正

這次我們透過VSCode提供的SonarLint，可以讓我們在開發時，就收到即時程式碼校正

## 安裝SonarLint

我們可以透過VSCode的延伸模組功能，透過搜尋SonarLint，找到該套件，並進行安裝，這樣就可以安裝完成了

## 設定SonarLint

輸入[Ctrl + ,]，可以直接進入到設定選單，然後我們在選單最上方搜尋欄位輸入以下字串進行搜尋

```
@ext:sonarsource.sonarlint-vscode
```

找到 sonarlint > connectedMode > connections: sonarqube 進入settings.json中編輯

在 sonarlint.connectedMode.connections.sonarqube 中，加入以下屬性，並設定成正確位置

```
{ 
    "serverUrl": "[你的SonarQube所在位置，例如：http://10.1.0.9:9000/]", 
    "token": "[你的user token，如何取得user token，下面有寫]" 
}
```

## 取得SonarLint User Token

1. 透過Web進入SonarQube的Web管理頁面，好比我是 [http://10.1.0.9:9000/](http://10.1.0.9:9000/)
2. 進入之後，先Login，如果你沒修改過你的預設帳密，你的帳密應該會是如下

![/blog/images/202102252253.png](/blog/images/202102252253.png)

```
帳號: admin
密碼: admin
```

{:start="3"}
3. 進入 我的帳號

![/blog/images/202102252258.png](/blog/images/202102252258.png)

{:start="4"}
4. 進入 安全

![/blog/images/202102252303.png](/blog/images/202102252303.png)

{:start="4"}
4. 輸入你的token名字，並按下確定

![/blog/images/202102252308.png](/blog/images/202102252308.png)

{:start="5"}
5. 將你的User Token貼回Vscode的settings.json中

## 程式碼即時檢驗

程式碼當中，如果有可以修改得比較具有可讀性時，會跳出提示

![/blog/images/202102252324.png](/blog/images/202102252324.png)