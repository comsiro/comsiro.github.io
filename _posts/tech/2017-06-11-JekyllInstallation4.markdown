---
layout: post
title:  간단한 Jekyll 설치 및 사용(4)
date:   2017-06-11 05:56:12 +1200
categories: tech
---

<a href="{{ site.github.url }}/tech/2017/06/11/JekyllInstallation3.html" class="page-change">이전 글</a>

<h1>- 더 나은 활용을 위해 필요한 기술들(선택)</h1>

<h1>1. Gulp를 통한 Browser-sync</h1>
Jekyll을 설치할때 같이 설치한 Bundle로도 블로그 수정시 자동으로 페이지를 수정하고 컴파일 하는 것이 가능합니다. 하지만 컴파일 후에 매번 브라우저를 다시 선택해 새로고침을 해 주어야 하는 불편함이 있습니다. 그럴때 사용할 수 있는 것이 Browser-sync 입니다. gulp watch와 browser-sync의 reload 기능을 통해 소스 코드가 변경될 시 브라우저를 자동으로 새로고침 해 줍니다. Browser-sync는 NPM, Webpack, Gulp, Grunt에서 다 지원하지만 이 글에서는 Gulp를 통해 사용하는 방법에 대해 설명하겠습니다.

- Gulp란?

Gulp는 자바스크립트(Javascript) 도구(혹은 모듈) 중에 하나 입니다. 비슷한 기능의 다른 유명한 도구로는 Grunt 등이 있습니다. NPM 패키지 매니저를 설치한 후 설치할 수 있습니다. NodeJS의 패키지 매니저의 이름이 NPM 입니다.(NodeJS에 관한 자세한 사항은 <a href="https://nodejs.org/ko/">nodejs 공식 사이트</a>에서 확인하시기 바랍니다.)

사실 NPM만 제대로 사용해도 왠만한 자바스크립트(웹) 프로젝트를 진행하는데 큰 문제는 없습니다. 다만 Gulp에서 지원하는 추가적인 기능들 때문에 Gulp를 많이 사용하고 있는 것 같습니다.

NPM을 통해 할 수 있는 빌드를 위한 거의 모든 기능을 Gulp를 통해서 할 수 있습니다. 여기서는 NPM은 프로젝트 관리 도구이고 Gulp는 빌드를 도와주는 도구 다 라는 정도로 알고 지나가면 되겠습니다. Gulp에 대한 자세한 사항은 <a href="http://gulpjs.com/">gulpjs 공식 사이트</a>를 참고하시기 바랍니다.

- Gulp 설치

먼저 <a href="https://nodejs.org/ko/">nodejs 공식 사이트</a>에서 자신의 OS에 맞는 NPM 설치 패키지를 다운받아 설치합니다. 그 후 <a href="http://gulpjs.com/">gulpjs 공식 사이트</a>에 나온대로 설치하면 됩니다. 설치를 완료하고 "gulp -v"를 리눅스 셸이나 윈도우 명령 프롬프트에 입력했을때 버전이 출력되면 정상적으로 설치가 완료된 것 입니다.

- Jekyll을 위한 Gulp 스크립트

본인의 프로젝트 폴더에 가서 "npm init"을 실행해 package.js 파일을 생성하고 다시 gulpfile.js 파일을 생성합니다. 그 후 아래의 코드를 gulpfile.js에 추가합니다.

{% highlight shell %}
/* 걸프 모듈을 둘러와 gulp라는 변수에 할당합니다. */
var gulp = require('gulp');

/* 걸프-셸 모듈을 둘러와 shell이라는 변수에 할당합니다. */
var shell = require('gulp-shell')

/* 브라우저-싱크 모듈을 둘러와 인스턴스를 생성하고 browserSync이라는 변수에 할당합니다. */
var browserSync = require('browser-sync').create();

/* build라는 이름의 걸프 태스크를 등록하고 태스크 호출시 실행될 shell 태스크를 지정합니다. */
gulp.task('build', shell.task(['bundle exec jekyll build --watch']));

/* serve라는 이름의 걸프 태스크를 등록하고 호출시 실행될 함수를 정의합니다.
그 함수에서는 브라우저-싱크를 초기화하고 서버의 디렉터리를 설정한 후
걸프 와치를 호출해 _site 디렉터리 안의 모든 폴더의 파일의 변경을 관찰해 
변경(change)가 발견될 경우 브라우저싱크의 리로드 메소드를 실행시킵니다. */
gulp.task('serve', function() {
   browserSync.init({server: {baseDir: '_site/'}});
   gulp.watch('_site/**/*.*').on('change', browserSync.reload);
});

/* 걸프 실행시 build와 serve라는 태스크를 실행합니다. */
gulp.task('default', ['build', 'serve']);

{% endhighlight %}

주석을 달아 두었지만 조금 더 자세히 설명하겠습니다. 모듈을 불러오는 부분은 그냥 그렇게 이해하고 지나가면 됩니다.

아래 라인은 "bundle exec jekyll build --watch"라는 커맨드 명령어(또는 셸 명령어)를 걸프 태스크로 실행합니다. 해당 명령어는 윈도우의 커맨드 포롬프트나 리눅스 셸에서 실행해도 바로 동작합니다. 의미는 루비(Ruby)의 bundle에게 Jekyll build를 실행하라는 의미이고 --watch 옵션은 페이지가 변할때마다 자동으로 마크다운(markdown) 파일을 컴파일 하라는 의미입니다.

{% highlight shell %}
gulp.task('build', shell.task(['bundle exec jekyll build --watch']));
{% endhighlight %}

아래 라인이 이 포스트에서 설명하고자 하는 핵심입니다. 주석으로 설명했다시피 브라우저싱크를 통해 로컬서버의 기본 디렉토리를 설정하고 변경시 자동으로 브라우저를 새로고침 하는 것 입니다.

{% highlight shell %}
gulp.task('serve', function() {
   browserSync.init({server: {baseDir: '_site/'}});
   gulp.watch('_site/**/*.*').on('change', browserSync.reload);
});
{% endhighlight %}

위에 걸프를 실행해서 빌드와 브라우저 새로고침을 자동화하는 것과 매번 수정하고 새로고침을 하는 것과는 개발시간에 엄청난 차이가 납니다.

<h1>2. SASS 활용</h1>
웹 개발에 대한 지식이 조금이라도 있는 사람이라면 CSS가 무엇인지는 한번쯤 들어봤을 것이라 생각합니다. SASS는 CSS 파일을 조금 더 효율적이고 신속하게 작성할 수 있도록 도와주는 언어입니다.

많은 Jekyll 테마들이 SASS를 사용하여 제작되었으므로 SASS 언어를 이해한다면 방문자에게 보여지는 페이지의 디자인을 손 쉽게 변경할 수 있습니다. 전 세계의 많은 프론트-엔드 개발자들이 이미 SASS를 사용하고 있습니다.

SASS에 대한 자세한 사항은 <a href="http://sass-lang.com/">SASS 공식 페이지</a>에 접속해서 확인하기 바랍니다.

<a href="{{ site.github.url }}/tech/2017/06/11/JekyllInstallation3.html" class="page-change">이전 글</a>