---
layout: post
comments: true
title:  Angular CLI에서 SASS 사용하기
date:   2017-06-13 06:10:00 +1200
categories: tech
---

오늘은 Angular2에서 SASS를 사용하는 방법을 간단히 정리해 보겠습니다.

참고로 Angular2는 Angular1을 기반으로 쓰여진 프래임워크(framework)가 아니라 새로 쓰여졌다고 하네요. Angular2에서 Typescipt를 사용하게 되므로써 Microsoft와 Google의 만남이라고 까지 말할 수 있을 것 같습니다.

새로운 언어나 프래임워크가 나왔다고 하던 공부를 다 접고 새로 시작할 필요는 없습니다만 요즘 최신 트렌드에 대해서 알아두는 것도 나쁘지 않습니다.

Angular와 Typescript에 대한 자세한 사항은 아래 링크에서 확인하세요.

<a href="https://angular.io/">Angular 공식 사이트</a>

<a href="https://www.typescriptlang.org/">Typescript 공식 사이트</a>

<hr>

이제 본론으로 들어갑니다.

angular-quickstart 프로젝트를 github에서 clone해서 수정할 수도 있겠지만 더 빠른 방법인 angular cli를 이용하여 로컬에 프로젝트를 생성하겠습니다. 아래 내용은 제일 아래 하단 참고 사이트들을 기반으로 쓰여졌습니다.

<h1>- npm을 이용해 angular cli 설치</h1>

npm의 설치법은 <a href="https://nodejs.org/ko/">nodejs 공식 사이트</a>에서 확인하시기 바랍니다.

{% highlight shell %}
/* npm을 통해 angular cli을 설치합니다.
여기서 -g 옵션은 특정 프로젝트에서만이 아니라 어느 위치에서든 실행할 수 있도록 설치하는데 사용하는 파라미터입니다.
--style=scss는 scss를 사용하는 프로젝트를 생성하라는 파라미터입니다. */
npm install -g @angular/cli --style=scss

/* 새로운 프로젝트를 생성합니다. 폴더도 같이 생성되므로 사전에 만들어 놓을 필요 없습니다. */
ng new [your project name]

/* 프로젝트 폴더로 이동합니다. */
cd [your project name]

/* angular 프로젝트를 컴파일하고 로컬 서버를 실행시킵니다.*/
ng serve
{% endhighlight %}

Browser를 통해 localhost:4200에 접속하면 프로젝트가 성공적으로 생성되고 서버에서 호스팅되고 있는 것을 확인할 수 있습니다.

<h1>- npm을 이용해 bootstrap4 설치</h1>

아래 명령어로 boostrap4를 설치합니다. 여기서 --save-dev는 개발 환경에서 사용하도록 저장하고 설치하라는 파라미터입니다.

{% highlight shell %}
npm install bootstrap@next --save-dev
{% endhighlight %}

.angular-cli.json 파일에 아래 부분에 node bootstrap 모듈을 추가합니다.

{% highlight shell %}
"styles": [
    "../node_modules/bootstrap/scss/bootstrap.scss",
    "styles.scss"
],
{% endhighlight %}

<h1>- 확인</h1>
app.component.html 파일에 아래 내용을 추가하고 브라우저에서 변경을 확인합니다.

{% highlight shell %}
<div>
  <button class="btn btn-secondary">{{title}}</button>
</div>
{% endhighlight %}



참고 : <a href="https://cli.angular.io/">Angular cli 공식 사이트</a>, <a href="https://github.com/angular/angular-cli/wiki/stories-include-bootstrap">Angular cli에서 bootstrap 사용하기 wiki</a>