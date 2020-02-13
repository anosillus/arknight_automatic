arknight
==============================

A short description of the project.

Project Organization
------------

ソシャゲの自動化をdocker上から出来るか試した。
required
- docker-compose
- docker
- android本体
- linux(windows, macでも多分動く)


how
- dockerでusbをマウントして、docker内のadbからpythonで操作.
- 画像認識は類似度で評価している。


問題
- イベント開始などでトップに強制移動されると無理になる(スクリプトは自動止する)
- tesseracの文字認識がそんなに上手くいかない。
- 高度な(完全)自動化、出来なくななさそうだが工数かかりそうなのでやってない。
- そもそもソシャゲ、UI設計以外に興味がない
--------

<p><small>Project based on the <a target="_blank" href="https://drivendata.github.io/cookiecutter-data-science/">cookiecutter data science project template</a>. #cookiecutterdatascience</small></p>
