---
layout: post
comments: true
title:  Nodejs version management- 노드제이에스 버전 관리
date:   2019-10-27 15:38:00 +1300
categories: js
---

<div class="post-head">
    <img src="{{ site.url }}/assets/images/Nodejs2.png" alt="Node.js Logo"/>
    <p class="image-description">- Node.js 로고 -</p>
</div>

<a href="https://nodejs.org/ko/">Nodejs 공식 사이트</a>

오늘 오랫만에 윈도우 머신에서 코딩을 하다가 n이 설치가 안되어 있어서 당황했는데요. 알고보니 n은 Windows 운영체제는 지원하지 않는다고 하네요.

n은 OSX나 Linux에서 동작하는 노드제이에스 버전 관리 툴입니다. 개발을 하다보면 최신 버전을 사용할때도 있고 예전 버전을 사용해야 할 경우도 생깁니다. 가령 오늘 제가 오늘 윈도우 머신에서 제킬 블로그를 업데이트하려다 보니 Gulp툴이 노드 버전 10에서 에러가 발생한것처럼 말이죠. 이럴때 N을 통해 간단하게 버전을 바꿔서 사용할 수 있습니다.

비슷한 툴로 NVM for Windows가 있는데요. 보통 노드제이에스를 설치할때 설치할 것인지 물어보는데 저는 설치를 안했었네요ㅎㅎ NVM은 윈도우에서도 잘 동작합니다. 아니 정확히는 윈도우용 프로젝트가 별도로 존재한다는 말이 맞겠네요.

<h4>
<a href="https://github.com/tj/n">N Git에 방문해서 더 알아보기</a>
</h4>
<h4>
<a href="https://github.com/nvm-sh/nvm">NVM Git에 방문해서 더 알아보기</a>
</h4>

- 추가
알고보니 natives만 설치하면 노드 버전 10 에서도 Gulp가 정상 동작하네요ㅋ

{% highlight shell %}
npm install natives
{% endhighlight %}