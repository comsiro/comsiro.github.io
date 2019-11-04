---
layout: post
comments: true
title:  VS2019을 통해 닷넷코어3 웹앱을 Azure VM에 배치하기
date:   2019-11-4 21:36:00 +1300
categories: dotnet
---

<a href="https://github.com/aspnet/Tooling/blob/AspNetVMs/docs/create-asp-net-vm-with-webdeploy.md">원문 참조하기</a>

아래 내용은 위의 링크를 따라 진행한 것을 제 경험을 보태서 적어 놓았습니다. 적용하다 헷갈리는 분은 원문을 참조해 주세요. 해당 글에서는 Azure에 가입하고 Subscription을 어떻게 생성하는지에 대해서는 다루지 않습니다. 자세한 내용은 Azure웹사이트를 참조하세요. 처음 계정을 생성하면 무료로 300 Credit을 주는데 왠만한건 다 해 볼 수 있습니다.

제목은 비주얼 스튜디오 2019을 이용한다고 했는데 정확하게는 MSDeploy를 이용해 어떻게 웹앱을 Deployment하냐가 정확할 것 같습니다. 설치는 크게 아래 순서대로 진행하였습니다.

1. Azure에 Win2019 VM 생성
2. IIS와 MSDeploy등 서버 구성
3. VS2019를 이용해 dotnet core 3 web app 프로젝트 생성하고 배치

<h2>
1. Azure에 Win2016 VM 생성하기
</h2>
<div class="center-image">
    <img src="{{ site.url }}/assets/images/az1.jpg" alt="create azure resource"/>
    <p class="image-description">- 애저에서 Windows server VM 생성하기 -</p>
</div>
<div class="center-image">
    <img src="{{ site.url }}/assets/images/az2.jpg" alt="create azure resource"/>
    <p class="image-description">- 애저에서 Windows server VM 생성하기 -</p>
</div>
윈도우즈 서버 이미지를 기본으로 가진 가상 머신을 만듭니다. 만들때 1 core에 3.5gb 램을 가진 Standard DS1 v2 이상을 선택해야 서버가 원할하게 동작합니다. 서버 버전은 쉽게 진행하기 위해 2016이나 2019을 추천합니다.

생성할때 웹 서비스를 운영할 수 있도록 80번 포트나 443포트를 오픈해 주는 것이 좋습니다. 윈도우즈에서 간단하게 RDP로 접속하기 위해서 3389포트도 오픈해 줍니다. 다른 것들은 기본 셋팅대로 진행하면 됩니다.

<h2>
2. IIS와 MSDeploy등 서버 구성하기
</h2>
VM 생성이 완료되면 Webdeploy를 위해 8172 포트를 오픈해 주어야 합니다. 아래 이미지와 같이 VM에 Networking에 접속하여 "Add inbound port rule"을 추가하여 8172 포트를 오픈해 줍니다.
<div class="center-image">
    <img src="{{ site.url }}/assets/images/az3.jpg" alt="Open Firewall"/>
    <p class="image-description">- 애저에서 Windows server VM 설정하기 -</p>
</div>

 또 MSDeploy를 위해서는 DNS를 설정해 주어야 합니다. Overview로 가서 DNS 옆에 버튼을 클릭하면 테스트에 활용할 수 있는 DNS를 설정할 수 있습니다.

 <div class="center-image">
    <img src="{{ site.url }}/assets/images/sv1.jpg" alt="Server 설치"/>
    <p class="image-description">- 서버에서 IIS 등 구성 요소 설정 -</p>
</div>

 이제 위에 이미지와 같이 서버에 접속하여 Add rule and features를 이용해 IIS에 IIS management Console을 설치하세요. 아까 오픈한 RDP포트를 통해 서버에 접속할 수 있습니다. 위에 설정한 DNS주소나 IP주소를 사용해 접속할 수 있습니다. 닷넷 코어 최신버전을 같이 설치해 주면 좋지만 우리는 Dotnet core 3 앱을 서비스 할 것이므로 아래 링크에 접속해 dotnetcore 3 runtime과 hosting bundle을 설치합니다.

<a href="https://dotnet.microsoft.com/download/dotnet-core/3.0">닷넷코어 런타임 및 호스팅 번들</a>

 <div class="center-image">
    <img src="{{ site.url }}/assets/images/sv2.jpg" alt="Server 설치"/>
    <p class="image-description">- 서버에서 IIS 등 구성 요소 설정 -</p>
</div>

IE Enhanced Security 모드 역시 관리자는 자유롭게 접속할 수 있도록 off해 주고 일반 사용자는 접속할 수 없게 on으로 설정합니다.

아래 링크로 접속하여 MSDeploy도 설치해 줍니다.
<a href="https://www.microsoft.com/en-us/download/details.aspx?id=43717">MS Deploy 설치 링크</a>

이제 서버 설정이 마무리 되었습니다.
<h2>
3. VS2019를 이용해 dotnet core 3 web app 프로젝트 생성하고 배치하기
</h2>

닷넷코어 웹앱 프로젝트를 생성합니다. 우리는 닷넷코어3을 사용할 것 입니다. 생성 후 IIS Express로 구동하여 정상 동작하나 확인합니다.

 <div class="center-image">
    <img src="{{ site.url }}/assets/images/vs-publish.jpg" alt="Server 설치"/>
    <p class="image-description">- 비주얼스튜디오에서 배치하기 -</p>
</div>

그 후 위의 이미지와 같이 배포 옵션을 선택합니다. Azure VM 배포를 선택하면 로그인 후 애저 서버에 접속해 VM을 선택할 수 있습니다. 여기서 가장 중요한 점은 꼭 Validate connection을 해줘야 한다는 것입니다. 서버 접속시 인증서를 다운받게 되어있는데 연결 검증을 하지 않으면 인증서를 다운받을 수 없습니다.

아까 Azure에 설정한 DNS를 설정해 주고 앱 배포를 합니다. 그 후 아무 브라우저나 열어 DNS를 입력하여 제대로 설치되었는지 확인하면 됩니다.

닷넷 코어는 모든 레퍼런스를 같이 배포할 수 있습니다. 그렇다고 런타임이 필요없는 것은 아니지만요.