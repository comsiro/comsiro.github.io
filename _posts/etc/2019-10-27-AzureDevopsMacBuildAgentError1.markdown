---
layout: post
comments: true
title:  Azure Devops 맥에서 빌드 에이전트 에러
date:  2019-10-27 15:16:00 +1300
categories: etc
---

애저 데브옵스에서 자마린(Xamarin) IOS 프로젝트를 빌드하기 위해서는 OSX가 동작하는 클라우드 호스트를 이용하거나 직접 Mac에 Build Agent를 설치해야 합니다.

그런데 Catalina 업그레이드 후 보안이 강하되어 Dll을 로드할때 마다 신뢰할 수 없는 다운로드된 파일이라는 경고가 뜨며 하나하나 예외를 추가해 주어야 합니다. 게다가 빌드 에이전트를 동작시킬때마다 반복해야 하여 매우 번거로운데요.

아래 명령어로 간단하게 모두 예외를 추가하면 보안에 구멍은 생기지만 더 이상 번거로운 작업들을 하지 않아도 됩니다.

{% highlight shell %}
sudo spctl --master-disable
{% endhighlight %}

<h4>
<a href="https://docs.microsoft.com/en-us/azure/devops/pipelines/agents/v2-osx?view=azure-devops">Self-hosted macOS agents에 대해 더 알아보기</a>
</h4>
