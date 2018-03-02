---
layout: post
comments: true
title:  Angular5 앱에 차트를 넣자. - Chart.js
date:   2018-03-03 01:08:00 +1300
categories: angular
---

<div class="post-head">
    <img src="{{ site.url }}/assets/images/chartjs.png" alt="Chart.js Logo"/>
    <p class="image-description">- Chart.js 로고 -</p>
</div>

<a href="http://www.chartjs.org/">Chart.js 공식 사이트</a>

<hr>

개발을 하다보면 차트 붙일 일이 많습니다. 오늘은 Chart.js를 사용해 차트를 캔바스에 그리는 예제입니다.
<br>
<br>
<h1>- 프로젝트 생성 후 Chart.js 설치</h1>
{% highlight shell %}
npm install chart.js --save
{% endhighlight %}

<h1>- 컴포턴트에 chart.js 모듈을 import 합니다.</h1>
{% highlight shell %}
import { Chart } from 'chart.js';
{% endhighlight %}

<h1>- View에 canvas를 추가합니다.</h1>
{% highlight shell %}
<div>
  <canvas #canvas>{{ chart }}</canvas>
</div>
{% endhighlight %}

<h1>- ViewChild를 통해 canvas 엘레먼트에 접근 2d context를 얻습니다.</h1>
{% highlight shell %}
@ViewChild("canvas") canvas: ElementRef;
    ...
let ctx = <HTMLCanvasElement>(this.canvas.nativeElement).getContext('2d');
{% endhighlight %}

<h1>- 차트를 준비합니다.</h1>
{% highlight shell %}
this.chart = new Chart(ctx, {
    ...
}
{% endhighlight %}

역시 가장 중요한 것은 ChangeDectorRef 의존성을 주입(DI)하고 값이 변경된 후 변경이 뷰에 반영되도록 하는 것 입니다. 자세한 코드는 <a href="https://github.com/comsiro/angular5-chartjs-example" target="_blank">Github</a>을 참고하세요.
<br>
<br>
소스 참고: 
<a href="http://tobiasahlin.com/blog/chartjs-charts-to-get-you-started/">TOBIAS AHLIN / BLOG</a>
