---
title: Tips on Deploying Hexo on GH Pages
date: 2020-02-05 16:29:19
tags:
---
由于现在Github对于免费版本已经不支持选择Page Source, 因此官方的CI Config Sample就不能很好的工作了. 官方的配置是将master branch下的所有原始文件编译至gh-pages branch下.

所以需要将.travis.yml做部分修改. 我新创建了staging branch作为写作的初始branch.
{% codeblock lang:xml Old version %}
branches:
  only:
    - master # build master branch only
...
deploy:
  on:
    branch: master
{% endcodeblock %}
{% codeblock lang:xml Updated version %}
branches:
  only:
    - staging # build staging branch instead
...
deploy:
  target_branch: master
  on:
  branch: staging
{% endcodeblock %}
