---
layout: post
title:  "如何用Jekyll + Github Page寫Blog"
date:   2020-10-07 00:00:00
categories: 程式語言
tags: Ruby
excerpt: 如何用Jekyll + Github Page寫Blog
mathjax: true
---

![](/blog/images/202010071248.jpg)

## 什麼是Jekyll
Jekyll是用Ruby寫的一套將Markdown內容轉成靜態HTML的工具，多數人都拿它來當寫Blog的工具

## 用Jekyll來寫Blog有什麼好處
1. 資料屬於自已，不用因為Blog商倒閉而所有辛苦寫的資料都不見
2. 所有資料都是靜態HTML+CSS+Javascript，可以扔到任何支援靜態網站的線上服務商，好比Github、IPFS
3. Markdown語法簡單易懂，不需要搞一堆有的沒的編輯器，沒有使用者管理，後台就是自已程式開發的IDE or Editor
4. 如果熟悉HTML、CSS、Javascript or 任一樣版語言的話，在修改網站上會比Wordpress這類需要理解它框架的Blog簡單許多
5. 資料整包帶著走，備份輕鬆，也可以透過Git做管理

## 安裝Jekyll
因為本人是用Majaro Linux，屬於Arch Linux系列，其他Linux我是參照官網的教學撰寫，並沒有實驗過，如果有任何問題，依官網安裝教學為準

Ubuntu
{% highlight console %}
sudo apt-get install ruby-full build-essential zlib1g-dev
{% endhighlight %}

Fedora
{% highlight console %}
sudo dnf install ruby ruby-devel @development-tools
{% endhighlight %}

Arch
{% highlight console %}
sudo pacman -S ruby base-devel
{% endhighlight %}

將Gem執行路徑加入Path參數

Ubuntu
{% highlight console %}
echo '# Install Ruby Gems to ~/gems' >> ~/.bashrc
echo 'export GEM_HOME="$HOME/gems"' >> ~/.bashrc
echo 'export PATH="$HOME/gems/bin:$PATH"' >> ~/.bashrc
source ~/.bashrc
{% endhighlight %}

Arch
{% highlight console %}
echo 'export PATH="${PATH}:$HOME/.gem/ruby/2.7.0/bin"' >> ~/.bashrc
{% endhighlight %}

其他Linux可以參照安裝完之後，Console跳的說明進行設定

安裝Jekyll
{% highlight console %}
gem install jekyll bundler
{% endhighlight %}

## 建置Blog
{% highlight console %}
# 新增Blog
jekyll new [你Blog的資料夾名稱]

# 運行Blog
cd [你Blog的資料夾名稱]
jekyll serve
{% endhighlight %}

打開你的瀏覽器，進入(http://localhost:4000)[http://localhost:4000]，如果有東西就算成功了

![](/blog/images/202010071344.png)

## Jekyll 指令
{% highlight console %}
# 新增一個專案
jekyll new PATH

# 新增一個空白專案
jekyll new PATH --blank

# 編譯網站(會將網站編譯到./_site)
jekyll build

# 運行網站（會先進行編輯之後，開啟HTTP Server，4000 Port，可以修改完即時看見結果)
jekyll serve

# 清除所有新增檔案(會清除所有由Jekyll所編譯新增的檔案，但會留下定義檔)
jekyll clean

# Jekyll 指令說明
jekyll help

# 新增Jekyll佈景
jekyll new-theme

# 輸出沒用到的套件與設定
jekyll doctor
{% endhighlight %}

## 套用佈景
Jekyll的佈景主題很多，以下網站可以找到不少別人設計好的佈景主題供我們套用

1. [jamstackthemes.dev](https://jamstackthemes.dev/ssg/jekyll/)
2. [jekyllthemes.org](http://jekyllthemes.org/)
3. [jekyllthemes.io](https://jekyllthemes.io/)
4. [jekyll-themes.com](https://jekyll-themes.com/)

一般來說，大多只要找到你們的佈景主題上的Github之後，將對方的Github Repository給Fork到你的Github就可以了，然後我們再將自已Fork的Repository給Clone下來

Clone下來之後，進入你Clone下來的資料夾，下運行Blog指令，如果沒有跳任何Error，就算成功了
{% highlight console %}
cd [你Clone下來的資料夾]
jekyll serve
{% endhighlight %}

最後，你就可以用這份檔案進行修改了

等等，那之前透過jekyll new新增的資料夾呢？
那是給你測試用的，如果你要自已設計佈景主題，可以從那個資料夾開始，不然就刪掉它吧

## 資料夾結構
index.html 你的Blog的主要Layout

_config.yml 你的Blog相關設定檔，好比標題、副標題、網址、base url等等

_posts 你的Blog的內容

_site 編譯後的網站內容

其他依不同的佈景主題，資料夾內容可能會有所增減

## 新增靜態資料存放資料夾
有時，我們可能會需要有可以放圖片的資料夾，我們可以透過以下方式進行新增

好比我在./底下，新增一個images的資料夾，那我必須將以下設定新增到./_config.yml裡面
{% highlight yaml %}
defaults:
  - scope:
      path: "images"
    values:
      image: true
{% endhighlight %}

接下來你就能透過/image/[你的圖片名字]載入圖片了

## 發佈到Github Page
1. 將你的網站整包透過Git放上你的Github Repository
2. 進入你的Githuab Repository
3. 點 Setting 進入
4. 將Repository name修改成你所需要的名字，好比Blog
5. 設定你要拿來當網站的Branch與網站根目錄
![](/blog/images/202010071637.png)
6. 之後等1到5分鐘之後，進入[https://你的帳號.github.io/你的Repository名字/](https://你的帳號.github.io/你的Repository名字/)就可以看見你的Blog了

但是這時你會發現，似乎所有的CSS、Javascipt、Image都抓不到，所以這時我們要到_config.yml設定

好比這是我的_config.yml的內容，其他依使用的佈景主題不同，_config.yml中的內容可能也會有所不同
{% highlight yaml %}
# Site settings
title: 達人手札 v2.0
brief-intro: 輕描淡寫|不求奢華
baseurl: "/blog" # the subpath of your site, e.g. /blog
url: "https://teed7334-restore.github.io" # the base hostname & protocol for your site
{% endhighlight %}

url就是設定你的Github Page的主機位置

baseurl就是設定你的Repository名字

而當我們的設定變動了之後，之前存放檔案的路徑也會有所變動
{% highlight console %}
# 之前插入圖片的語法
![](/images/xxx.png)

# 之後插入圖片的語法
![](/你的Repository名字/images/xxx.png)
{% endhighlight %}

而之後你用Jekyll Serve開啟服務器之後，你的網址也將變成
[https://localhost:4000/你的Repository名字/](https://localhost:4000/你的Repository名字/)

如果本地端還有一些css、javascript顯示上的問題的話，可以自已去修改佈景主題檔

之後，不管你有任何修改還是撰寫新的Blog，只要將檔案Git Push上Githuab就好，大約過1到5分鐘，Github Page上的內容就會變動了

## 關於highlight
Jekyll的highlight是用Rouge這項套件做到的，在程式碼色彩高標上面用法和一般markdown有些許不同

![](/blog/images/202010071718.png)

其它關於Rouge的功能與支援的語系，請參照如下

1. [rouge](http://rouge.jneen.net/)
2. [jekyll rouge](https://jekyllrb.com/docs/liquid/tags/#code-snippet-highlighting)