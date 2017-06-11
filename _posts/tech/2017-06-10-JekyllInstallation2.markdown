---
layout: post
title:  간단한 Jekyll 설치 및 사용(2)
date:   2017-06-10 07:16:12 +1200
categories: tech
---

<a href="{{ site.url }}/tech/2017/06/10/JekyllInstallation1.html" class="page-change">이전 글</a>
<a href="{{ site.url }}/tech/2017/06/11/JekyllInstallation3.html" class="page-change">다음 글</a>

<h1>- 설치 및 간단한 사용 방법</h1>
아래에 내용은 Jekyll 공식 사이트의 내용을 기반으로 작성되었습니다.(<a href="https://jekyllrb-ko.github.io/">https://jekyllrb-ko.github.io/</a>)
<hr><br>

<h1>1. 루비 설치</h1>

<a href="https://www.ruby-lang.org/ko/downloads/">루비 다운로드 페이지</a>에 접속해 루비(Ruby)를 다운 받아 설치합니다. 버전은 현재 안정 버전으로 다운 받는 것이 가장 좋습니다. 자신의 컴퓨터 OS에 맞는 패키지를 다운로드 받아 사이트에 나온 가이드 대로 설치하면 됩니다. Ruby는 하나의 프로그램 언어 입니다. 하지만 Jekyll을 사용하는데 깊게 이해할 필요는 없습니다. Jekyll이 루비로 만들어 졌다는 것만 기억하고 지나가면 됩니다.

![루비 설치 중에 뜨는 화면1]({{ site.baseurl }}/assets/RubyInstallation1.jpg)
<hr><br>

<h1>2. MSYS2 설치</h1>

위 이미지 처럼 루비 설치를 완료하면 MSYS2를 설치할 것인지 선택하는 옵션이 나옵니다. 체크하고 Finish를 누릅니다. MSYS2는 여러분이 윈도우 커맨드 프롬프트(Window command prompt) 창에서도 루비 명령어를 실행하고 사용할 수 있도록 해 줍니다.(다른 운영체제를 사용하는 분들은 그 환경에 맞는 설치 방법이 루비 공식 사이트에 나와 있습니다.)

![루비 설치 중에 뜨는 화면2]({{ site.baseurl }}/assets/RubyInstallation2.jpg)

위 이미지에서 1 2 3 을 순차적으로 선택해 설치합니다. 설치를 완료하고 커맨드 프롬프트(Command Prompt)를 실행시켜 아래 이미지에 나온 명령어를 실행하여 Gem 버전이 나오면 바르게 설치된 것 입니다.

![루비 설치 중에 뜨는 화면3]({{ site.baseurl }}/assets/RubyInstallation3.jpg)

Gem은 루비를 사용하는데 필요한 라이브러리(Library)를 설치하고 관리하는데 도움을 주는 루비에서 사용하는 툴의 이름입니다. 자세한 내용은 <a href="http://ruby-korea.github.io/rubygems-guides/what-is-a-gem/">RubyGems의 공식 사이트</a>를 참고하세요.

윈도우 커맨드 프롬프트는 windows command key + R을 해 Run을 실행 시킨 후 cmd를 입력하고 엔터키를 누르면 실행됩니다. 마우스를 이용해 윈도우 시작 버튼으로 가서 찾아 선택하는 방법도 있겠으나 개발의 생산성 향상을 위해 단축키 사용을 미리 연습해 두는 것이 좋습니다. 윈도우와 크롬 단축키에 관한 내용은 <a href="{{ site.url }}/tech/2017/06/11/WindowsChromeShortcut.html">윈도우, 크롬 단축키</a>를 참고하세요.

자 이제 Jekyll을 설치할 준비가 되었습니다.
<hr><br>

<h1>3. JeKyll 설치</h1>

윈도우즈 커맨드 프롬프트에서 아래 명령어를 실행합니다.

{% raw %}
gem install jekyll
{% endraw %}

제가 자세한 사항을 적으려다 공식 사이트를 참조하려고 보니 이미 훌륭한 한글 번역 문서가 있네요.
<a href="http://jekyllrb-ko.github.io/docs/installation/">Jekyll 공식 설치 가이드</a>를 참조해서 설치를 완료하세요.

다음 장에서는 Github 페이지에 업로드하는 방법에 관한 포스트를 적어보도록 하겠습니다.

<a href="{{ site.url }}/tech/2017/06/10/JekyllInstallation1.html" class="page-change">이전 글</a>
<a href="{{ site.url }}/tech/2017/06/11/JekyllInstallation3.html" class="page-change">다음 글</a>