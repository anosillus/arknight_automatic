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
- dockerでusbをマウントして、docker内のadbからpythonで操作
- 画像認識は類似度で評価している。

問題
- イベント開始、朝4時の更新でトップに強制移動されると、トップ画面からの画面遷移作ってないので無理になる(スクリプトは停止する)
- tesseracの文字認識がそんなに上手くいかない。
- 複数端末の操作は対応させてない、多分出来るし、お金にするならそういうの対応させるべきだと思う(しませんが)
- 高度な(完全)自動化、出来なくななさそうだが工数かかりそうなのでやってない。
- ソシャゲ、UI設計以外には興味がない
--------

<p><small>Project based on the <a target="_blank" href="https://drivendata.github.io/cookiecutter-data-science/">cookiecutter data science project template</a>. #cookiecutterdatascience</small></p>
