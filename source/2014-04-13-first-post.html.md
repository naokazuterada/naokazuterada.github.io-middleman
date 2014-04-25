---
title: First Post
date: 2014/04/13
category: update
---

ブログなんて何年ぶりかわからないけど、気になっていた[Jekyll](http://jekyllrb.com/)の勉強がてらはじめてみることにしました。記憶からこぼれ落ちそうな内容を、書き留めておく場所にしようかな？と思ったので、タイトルは「Out of My Memory」としてみます。

さっそく、jekyll newした時に問題発生したので書き留めておきます。

```sh
$ jekyll new mysite

  SafeYAML Warning
  ----------------

  You appear to have an outdated version of libyaml (0.1.4) installed on your system.

  Prior to 0.1.6, libyaml is vulnerable to a heap overflow exploit from malicious YAML payloads.

  For more info, see:
  https://www.ruby-lang.org/en/news/2014/03/29/heap-overflow-in-yaml-uri-escape-parsing-cve-2014-2525/

  The easiest thing to do right now is probably to update Psych to the latest version and enable
  the 'bundled-libyaml' option, which will install a vendored libyaml with the vulnerability patched:

  gem install psych -- --enable-bundled-libyaml

```

rbenvを使っていたので、普通にrbenv installでまだ入れてなかった2.0.0を入れてから試してもダメだったので、変だと思ったのですが、
探すと[stackoverflow](http://stackoverflow.com/questions/22919318/fix-for-prior-to-0-1-6-libyaml-is-vulnerable-to-a-heap-overflow-exploit-from-m)に解決方法を書いてくれている人がいました。ありがたい。

まず、ruby-buildを更新してからrubyをビルドするとうまくいくようです。

```sh
$ rm -rf ~/.rbenv/plugins/ruby-build
$ git clone https://github.com/sstephenson/ruby-build.git ~/.rbenv/plugins/ruby-build
$ rbenv install 2.0.0-p451
```

自分がどうしたか忘れましたが（さっそく…）、このあとにJekyllをインストールしてあげれば間違いないと思います。


# My first impression of Jekyll

- 最初は、Gemfileに色々書いて言ってたんだけど、github-pagesというのだけ入れればよかった。
- Github Pagesで運用する場合はconfigにsourceの指定しても無効で、[必ずルートに設定を上書きされるらしい](https://help.github.com/articles/using-jekyll-with-pages#configuration-overrides)。
- まだ１つしか記事書いてないが、全体のスタイルなどの更新と、記事の更新がcommit上で一緒くたになってしまうのが、若干気持ち悪いかなぁ…