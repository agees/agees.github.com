# encoding: utf-8
---
layout: post
title: "1st : start up!"
date: 2012-02-09 22:43
comments: true
categories: 
---

なにはともあれRailsやってみよう  
  <!-- more -->
今日やること
-----
+ vimに触ってみる
+ Rails動かしてみる
+ gitを使ってみる

環境設定
-----
1. Install vim  
  [`vim`](http://www.kaoriya.net/software/vim "vimダウンロード")  
  vimをダウンロードしてインストールする。
2. コマンドライン環境を作る  
  windowsにlinuxライクな使いやすいコマンドライン環境を作る。  
    + [Console2 + nyaos](http://efcl.info/2011/0501/res2717/ "Console2 + nyaos")  
    まずはConsol+nyaosをイン  
    [`Console2`](http://sourceforge.net/projects/console/ "Console2")  
    [`nyaos`](http://www.nyaos.org/index.cgi?p=DOWNLOAD_2xx "nyaos")  
    Console2を開い  
      `Edit->Settings->Tab->Shell`  
    にnyaos.exeのパスを指定すればOK。  
    + [nerdtree](http://www.vim.org/scripts/script.php?script_id=1658 "nerdtree")  
    その後にnerdtreeをインストする。  
    nerdtreeとはコンソールから使えるエクスプローラのようなvim拡張。便利。  
    [`nerdtree`](http://www.vim.org/scripts/download_script.php?src_id=17123 "nerdtree download")  
    落としたzipを解凍/vim/vimfilesに配置。  
    で、以下を`vimrc`に追記。  

        " 引数なしならNERDTree実行、ありならフツーにvim
        let file_name = expand("%")
        if has('vim_starting') &&  file_name == ""
            autocmd VimEnter * NERDTree ./
        endif

    vim.exeにパスを通すのもやっておく。
    
3. githubアカウントの  
    ソース管理にはgithubを使う。Railsのインストール時にアカウントが必要に  
    なるので以下でアカウントを作っておく。  
    [`github`](https://github.com/ "github")  
  
4. Install Rails  
  Railsをインストールする。  
  [`RailsInstaller`](http://railsinstaller.org/ "RailsInstaller")  
  この動画の通りなんだけども
  [![RailsInstaller](http://railsinstaller.org/images/video-thumbnail.png)](http://vimeo.com/34078037)  
  インストール後にgithubアカウントを登録する。  

Railsを動かしてみる
-----
  とりあえずRailsを動かしてみる。まずはバージョンの確認。
    $ rails -v
    Rails 3.1.1
  新規アプリケーションを作る。  
    $ rails new HelloRails
  動作確認してみる。  
    $ rails s
・ｱ・ｱ[`localhost:3000`](http://localhost:3000)みると
  こんなのが出る。
  ![firstpage](/images/scshot1.png)
  動いたねと。

githubにソースをアップしてみる
-----
1.  リポジトリを作る。  

    以下で`ProjectName`を入力して`Create Repository`する

    ![newrepo](/images/newrepo.png)
    
    すると手順のページが出るので、`$git init`以下をやる。
    
    ![newrepo_todo](/images/newrepo_todo.png)

2. first pushまで  

    git init  
        $ git init  
    git add  
        $ git add .  
    git commit  
        $ git commit -m 'first commit'  
    git remote  
        $ git remote add origin git@github.com:username/ProjectName.git  
    git push  
        $ git push -u origin master  

3. 見てみる  

    `github`の`YourRepositories`にさっき`git push`したプロジェクトが表示されていて、  
    中身が以下のようになっていればOK  

    ![helloagees](/images/helloagees.png)

DB連携のwebアプリをさらっと（余裕があれば）
-----

1.  scaffold  

    scaffoldを実行してみる。
    以下のコマンドをたたSQLITE（他DBに変更可能）上に
    tableとかcolumnを作成してくれて、しかも
    マスタメンテ的ページまで作成してくれる。

    +  scaffold  
    これをやると自動的にcontrollerとview(ページテンプレ)とmodel(dbアクセサ)まで勝手に作ってくれる。  

            $ rails g scaffold item code:string name:string description:text canceled:boolean  
    
    +  migrate  
    これやるとmodelを元にdbにtableを作成してくれたり、修正できたりする。  

            $ rake db;migrate  

    ※補足：間違ったら  
    `db/migrate/20120101~create_items.rb`  
    みたいのができているので、  
    それを直してもう一回`rake db:migrate`すればOK

2.  見てみる  
        $ rails s  
    して、`http://localhost:3000/items`をみるとこんなのが   

    ![itemsfirst](/images/itemsfirst.png)  

    `New Item`するとこんな感じ  

    ![newitemadd](/images/newitemadd.png)  

    `Create Item`して`Back`するとこんな感じでデータができている。  

    ![newitemed](/images/newitemed.png)  



    
