---
title: Transfer to MiddleMan
date: 2014/04/26
category: update
---

[Jekyll](http://jekyllrb.com/) みたいな静的サイトジェネレーターで「[MiddleMan](http://middlemanapp.com/)」というのを発見し、ブログ以外にも普段の仕事なんかでも使えるかなと思って、切り替えてみた。で、また色々つっかえたので書いとく。

つっかえた原因は、MiddleManのせいではなく、GithubPagesの仕様をちゃんと理解していなかったからだった。

GitHubPagesは、そのリポジトリがProjectのサイトなのか、UserまたはOrganizationのサイトなのかによって、若干仕様が違うらしい。Projectサイトの場合は、`gh-pages`ブランチのコンテンツが表示され、User/Organizationサイトの場合は、`master`ブランチのコンテンツが表示されるらしい[^1]。

[^1]: 参考 [middleman-blogをgithubでホストする / Coiney Developer Blog](http://blog.coiney.com/2013/06/21/host-middleman-blog-on-github/)

今回、middleman-deployを使って、`config.rb`で`gh-pages`ブランチをdeploy先に指定していたせいでサイトが表示されなくて困った。
前回までも、上記の仕様を知らずに、`gh-pages`ブランチを使っていたんだけど、どうもJekyllを使っていたからGitHub側できちんとdeployしてくれて表示ができていたということらしい。

変な仕様だなと思うんだけど、まぁ確かにプロジェクトの方はメイン（master）はプロジェクトのソースコードで、ユーザー／Organizationの方はサイトがメインと考えられるから、まぁ納得。でも、ちょっと気づきにくいなぁ。

あとは、`confg.rb`で

```rb
Time.zone = "Tokyo"
```

としてなくて、今書いてる記事がbuildされない（多分深夜だったからUTC時間では未来だと判定されたのだろう…）など、あったが、まぁ、まぁ。なにはともあれ、とりあえず公開までできたので、色々試していこうと思う。Jekyllでは、Octpressからコード整形プラグイン引っこ抜くなど、それなりに時間かかったんだけど、また振り出しです。がんばろー・・・っと。

注：なんだか、前回は「ですます調」で書いたんだけど、なんか疲れたのでこんな感じで・・・