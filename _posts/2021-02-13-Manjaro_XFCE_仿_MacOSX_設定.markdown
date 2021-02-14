---
layout: post
title:  "Manjaro XFCE 仿 MacOSX 設定"
date:   2021-02-13 00:00:00
categories: 軟體設定
tags: 軟體設定
excerpt: Manjaro XFCE 仿 MacOSX 設定
mathjax: true
---

![/blog/images/202102131313.png](/blog/images/202102131313.png)

其實我本人不太想抄MacOSX，我本來是想將桌面設定夜店風格，不過找到的佈景主題都不是很好，不是UI顯示得不清不楚，就是Icon少東少西，最後只好改用MacOSX Dark

MacOSX Dark UI配色

![/blog/images/202102131322.png](/blog/images/202102131322.png)

Sweet Dark UI配色

![/blog/images/202102131323.png](/blog/images/202102131323.png)

MacOSX Dark UI & Icons

![/blog/images/202102131334.png](/blog/images/202102131334.png)

Sweet Drak UI & Icons

![/blog/images/202102131335.png](/blog/images/202102131335.png)

就以清淅度與質感而言，MacOSX的配色與Icon都大勝其他的設計

## 設定佈景主題

下載地址-

[https://www.xfce-look.org/p/1275087/](https://www.xfce-look.org/p/1275087/)

我這邊是下載Mojave-dark.tar.xz

另外有一個MacOSX主題是For XFCE專用的，配色也比較明亮一些

[https://www.xfce-look.org/p/1207818/](https://www.xfce-look.org/p/1207818/)

我這邊是下載PRO-dark-XFCE-4.14.tar.xz

將下載之後的壓縮檔，直接解壓縮，放到~/.themes之後，到 應用程式/設定值/外觀/樣式(Y) 裡面，就可以找到該佈景了，並將其指定就設定完成了

## 設定小圖示

下載地址-

[https://www.xfce-look.org/p/1275087/](https://www.xfce-look.org/p/1275087/)

我這邊是下載01-McMojave-circle.tar.xz

將下載之後的壓縮檔，直接解壓縮，放到~/.icons之後，到 應用程式/設定值/外觀/圖示(I) 裡面，就可以找到該佈景了，並將其指定就設定完成了

這時我們可以在 應用程式 按鈕/右鍵/屬性(P)/面板按鈕(P)/圖示(I)，就可以設定應用程式按鈕的Icon了

我是不喜歡設成Apple的圖樣啦，覺得Linux的應用程式按鈕設定成Apple樣式有點不倫不類，所以我是用icon提供的manjaro圖示

~/.icons/McMojave-circle-dark/apps/scalable/start-here-manjaro.svg

## 設定滑鼠指標

下載地址-

[https://www.xfce-look.org/s/XFCE/p/1355701/](https://www.xfce-look.org/s/XFCE/p/1355701/)

我這邊是下載McMojave-cursors.tar.xz

將下載之後的壓縮檔，直接解壓縮，放到~/.icons之後，到 應用程式/設定值/滑鼠與觸碰板/主題(T) 裡面，就可以找到該佈景了，並將其指定就設定完成了

也可以到 應用程式/設定值/滑鼠與觸碰板/裝置(D) 裡面，將 反轉捲軸方向 打勾，就可以和MacOSX一樣，往下滾是向上滑，往上滾是向下滑

## 設定自動置換桌布

安裝Variety
```
sudo pacman -S variety
```

安裝完之後，開啟variety，並進入Preferences

1. 開啟自動啟動打勾
2. 每...多久換一張圖打勾，我自已是設每5分鐘
3. 圖庫來源任選一個或多個打勾，我自已是比較建議用unsplash，圖片品質普遍比較高

![/blog/images/202102131432.png](/blog/images/202102131432.png)

## 設定Dock

在設定Dock之前，我們先將面板移到上方去

可以透過 應用程式 按鈕/右鍵/面板(L)/面板偏好設定(E)/顯示/一般/鎖住面板(L) 的選項先取消，就可以將面板拖到上方去，拖上去之後再鎖定就好

![/blog/images/202102131443.png](/blog/images/202102131443.png)

安裝Plank
```
sudo pacman -S plank
```

安裝完之後，到 應用程式/設定值/工作階段與啟動/應用程式自動啟動(L) ，追加一個plank設定

![/blog/images/202102131448.png](/blog/images/202102131448.png)

並且打勾

![/blog/images/202102131449.png](/blog/images/202102131449.png)

## 設定Global menu

安裝所需之appmenu安裝包
```
pamac build vala-panel-git
pamac build vala-panel-appmenu-registrar-git
pamac build vala-panel-appmenu-budgie-git
pamac build vala-panel-appmenu-common-git
pamac build vala-panel-appmenu-xfce-git
pamac build vala-panel-appmenu-mate-git
pamac build vala-panel-appmenu-jayatana-git
pamac build vala-panel-appmenu-valapanel-git
pamac build appmenu-gtk-module-git
```

將App Menu移到Global menu
```
xfconf-query -c xsettings -p /Gtk/ShellShowsMenubar -n -t bool -s true
xfconf-query -c xsettings -p /Gtk/ShellShowsAppmenu -n -t bool -s true
```

重開機

## 設定albert

安裝albert
```
pamac build albert-git
```

安裝完之後，可以到 應用程式/附屬應用/albert 打開它

![/blog/images/202102131911.png](/blog/images/202102131911.png)

![/blog/images/202102131915.png](/blog/images/202102131915.png)

使用畫面

![/blog/images/202102131919.png](/blog/images/202102131919.png)

一些使用的小技巧

計算機

![/blog/images/202102131921.png](/blog/images/202102131921.png)

Hash

![/blog/images/202102131923.png](/blog/images/202102131923.png)

透過Google搜尋

![/blog/images/202102131924.png](/blog/images/202102131924.png)

最好用的功能莫過於知道應用程式名字，可以直接Key名字就啟動，簡直比滑鼠移過去還快啊

![/blog/images/202102131955.png](/blog/images/202102131955.png)

其它用法可以參照Albert的Extensions

## 設定視窗控制按鈕方向

進入 應用程式/設定值/視窗管理程式 做以下設定

![/blog/images/202102141121.png](/blog/images/202102141121.png)

## 設定字型

安裝類似Mac OSX字型
```
pamac build ttf-roboto
pamac build adobe-source-sans-pro-fonts
```

進入 應用程式/設定值/視窗管理程式 做以下設定

![/blog/images/202102141521.png](/blog/images/202102141521.png)

進入 應用程式/設定值/外觀 做以下設定

![/blog/images/202102141524.png](/blog/images/202102141524.png)

## 設定lightDM

安裝lightdm-webkit2-greeter
```
sudo pacman -S lightdm-webkit2-greeter
```

下載Aqua套件
```
git clone https://github.com/paysonwallach/aqua-lightdm-webkit-theme.git
```

將預設lightDM greeter改成lightdm-webkit2-greeter
```
sudo vim /etc/lightdm/lightdm.conf
```

將greeter-session改成如下
```
greeter-session=lightdm-webkit2-greeter
```

將Aqua套件的資料夾名稱改成aqua，複製到/usr/share/lightdm-webkit/themes

並指定權限如下
```
sudo chmod -R 755 aqua
```

將預設lightDM 佈景主題改成aqua
```
sudo /etc/lightdm/lightdm-webkit2-greeter.conf
```

將webkit-theme改成如下
```
webkit-theme = aqua
```

設定lightDM的背景圖
```
sudo ln -s [你想要拿來當背景圖的圖檔] /usr/share/backgrounds/current
```

重開機

![/blog/images/202102131945.png](/blog/images/202102131945.png)

![/blog/images/202102131946.png](/blog/images/202102131946.png)