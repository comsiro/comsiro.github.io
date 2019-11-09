---
layout: post
comments: true
title:  안드로이드 avd - Hyper-v 에러
date:   2019-11-10 07:02:00 +1300
categories: mobile
---

윈도우에서 아래와 같은 애러가 발생했을 경우 해당 머신이 VT-x를 지원하는지 설명서를 확인한 후 지원하면 바이오스셋업에서 VT-x를 사용으로 바꿔주어야 합니다. 그리고 만약 하이퍼 브이가 동작중이면 윈도우 서비스에서 관련 서비스들을 다 멈춰야 합니다.

This computer does not support Intel Virtualization Technology (VT-x) or it is being exclusively used by Hyper-V. HAXM cannot be installed. 
Please ensure Hyper-V is disabled in Windows Features, or refer to the Intel HAXM documentation for more information.