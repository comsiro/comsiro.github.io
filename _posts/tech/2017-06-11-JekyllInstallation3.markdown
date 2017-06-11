---
layout: post
comments: true
title:  간단한 Jekyll 설치 및 사용(3)
date:   2017-06-11 04:32:12 +1200
categories: tech
---

<a href="{{ site.github.url }}/tech/2017/06/10/JekyllInstallation2.html" class="page-change">이전 글</a>
<a href="{{ site.github.url }}/tech/2017/06/11/JekyllInstallation4.html" class="page-change">다음 글</a>

<h1>- Github에 업로드</h1>
아래 내용은 <a href="https://help.github.com/articles/using-jekyll-as-a-static-site-generator-with-github-pages/">Github 공식 사이트</a>의 내용을 기반으로 작성되었습니다.

앞의 글에 언급한 바와 같이 jekyll의 가장 큰 장점은 Github Page를 통해 내 블로그를 호스팅 할 수 있다는 것 인데요. 이것이 가능한 이유는 Jekyll이 DB를 사용하지 않기 때문 입니다. 서버쪽에서 처리해야 할 것이 기본적인 웹 서버의 기능 말고는 거의 없기 때문에 소스코드를 공개하고 깃헙에서 무료로 블로그를 운영할 수 있는 것이지요.
<hr><br>

<h1>1. Github에 프로젝트 생성</h1>

<a href="https://github.com/">Github</a>에 접속해 계정을 만들고 <a href="https://github.com/new">새로운 프로젝트</a>를 생성합니다. 이때 프로젝트 이름(Repository name)은 <span class="highlight">[나의 깃헙 아이디].github.io</span>로 합니다.

![새 프로젝트 생성]({{ site.github.url }}/assets/images/Github1.jpg)

<hr><br>

<h1>2. 로컬의(자신의 컴퓨터의) 프로젝트 폴더에 github 프로젝트 연동</h1>

프로젝트를 생성하고 나면 아래처럼 하라고 친절히 Github에서 알려 줍니다. 자신의 Jekyll 프로젝트 폴더로 가서 아래를 실행합니다.

{% highlight shell %}
git init
git add README.md
git commit -m "1st commit"
git remote add origin https://github.com/[나의 GitHub 아이디]/[나의 GitHub 아이디].github.io.git
git push -u origin master
{% endhighlight %}

<br>

연동이 완료되었습니다. 브라우저 창에 주소를 입력하면 나의 블로그가 보입니다.

![내 블로그]({{ site.github.url }}/assets/images/Github2.jpg)

다음 장에서는 Jekyll을 더 잘 활용하기 위해 필요한 기술들에 대해 적어보겠습니다. 선택 사항이지만 웹 개발에 관심이 있는 분들은 그냥 지나치지 말고 읽고 지나가면 도움이 될 것 같습니다.

<a href="{{ site.github.url }}/tech/2017/06/10/JekyllInstallation2.html" class="page-change">이전 글</a>
<a href="{{ site.github.url }}/tech/2017/06/11/JekyllInstallation4.html" class="page-change">다음 글</a>