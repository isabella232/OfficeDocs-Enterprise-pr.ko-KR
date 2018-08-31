---
title: Office 365 네트워크 연결 원칙
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 6/14/2018
ms.audience: Admin
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
search.appverid: MET150
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.assetid: 76e7f232-917a-4b13-8fe2-4f8dbccfe041
description: Office 365 네트워크 연결에 대 한 네트워크 계획을 시작 하기 전에는 안전 하 게 Office 365 트래픽을 관리 하 고 사용 가능한 최고의 성능을 연결 원칙을 이해 하는 것이 중요 합니다. 이 문서는 안전 하 게 Office 365 네트워크 연결을 최적화 하는 것에 대 한 최신 지침을 이해 하는데 도움이 됩니다.
ms.openlocfilehash: be41162833a7442ac65af1e973a00923841fca6b
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/27/2018
ms.locfileid: "22542073"
---
# <a name="office-365-network-connectivity-principles"></a>Office 365 네트워크 연결 원칙

Office 365 네트워크 연결에 대 한 네트워크 계획을 시작 하기 전에는 안전 하 게 Office 365 트래픽을 관리 하 고 사용 가능한 최고의 성능을 연결 원칙을 이해 하는 것이 중요 합니다. 이 문서는 안전 하 게 Office 365 네트워크 연결을 최적화 하는 것에 대 한 최신 지침을 이해 하는데 도움이 됩니다.
  
기존 엔터프라이즈 네트워크는 사용자가 응용 프로그램 및 강력한 경계 보안으로 운영 하는 회사 데이터 센터에서 호스팅되는 데이터에 대 한 액세스를 제공 하는 기본적으로 설계 되었습니다. 기존 모델 지점에서 WAN 링크를 통해 또는 원격으로 VPN 연결을 통해 응용 프로그램 및 회사 네트워크 경계 내에서 데이터 사용자 액세스를 가정 합니다. 
  
SaaS 응용 프로그램 서비스와 네트워크 경계 밖에 있는 데이터의 일부 조합을 이동 하는 Office 365와 동일 하 게 채택 합니다. 최적화를 사용 하지 않으면 사용자와 SaaS 응용 프로그램 간의 트래픽은 패킷 검사, 네트워크 hairpins, 지리적으로 멀리 떨어져 있는 끝점에 대 한 의도 하지 않은 연결 및 기타 요인에 의해 정의 된 대기 시간에 따라 달라 집니다. 최상의 성능을 위해서는 Office 365 및 이해 하 고 중요 한 최적화 지침을 구현 하 여 안정성을 보장할 수 있습니다.
  
이 문서에 대해서 설명 합니다.
  
- 클라우드로 고객 연결에 적용 하는 것으로 [office 365 아키텍처](office-365-network-connectivity-principles.md#BKMK_Architecture)
- 업데이트 된 [Office 365 연결 원칙](office-365-network-connectivity-principles.md#BKMK_Principles) 및 네트워크 트래픽 및 최종 사용자 경험을 최적화 하기 위한 전략
- [Office 365 끝점 웹 서비스를](office-365-network-connectivity-principles.md#BKMK_WebSvc)네트워크 관리자가 네트워크 최적화에 사용 하기 위해 끝점의 구조화 된 목록 사용 (영문)를 허용 하는
- [새로운 Office 365 끝점 범주](office-365-network-connectivity-principles.md#BKMK_Categories) 및 최적화에 대 한 지침
- [끝점 보안이 포함 된 네트워크 경계 보안 비교 (영문)](office-365-network-connectivity-principles.md#BKMK_SecurityComparison)
- Office 365 트래픽에 대 한 [증분 최적화](office-365-network-connectivity-principles.md#BKMK_IncOpt) 옵션

## <a name="office-365-architecture"></a>Office 365 아키텍처
<a name="BKMK_Architecture"> </a>

Office 365 란 마이크로 서비스 및 Microsoft 비즈니스 온라인 상태에 대 한 Exchange Online, SharePoint Online Skype 등의 응용 프로그램의 다양 한 집합을 통해 생산성 및 공동 작업 시나리오를 제공 하는 분산된 소프트웨어--a-서비스로 (SaaS) 클라우드 팀, Exchange Online Protection, Office Online 및 다른 많은 합니다. 특정 Office 365 응용 프로그램 고객 네트워크 및 클라우드에 대 한 연결에 적용 자신의 고유한 기능을 가질 수 하는 동안 일부 주요 보안 주체, 목표 및 아키텍처 패턴 공유할 모든 있습니다. 이러한 사용자와 연결에 대 한 아키텍처 패턴은 플랫폼으로-서비스 및 Microsoft와 같은 인프라--a-서비스로 구름의 일반적인 배포 모델에서 다른 작업은 상당히 되 고 동시에 및 다른 많은 SaaS 구름 모양에 대 한 일반적인 Azure 합니다.
  
Office 365 (즉 종종 부재중 또는 네트워크 기획자 하 여을 잘못 해석)의 가장 중요 한 아키텍처 관련 기능 중 하나는 것은 사용자에 연결 하는 방법의 컨텍스트에서 실제로 글로벌 분산된 서비스입니다. 대상 Office 365 테 넌 트의 위치는 클라우드 내에서 고객 데이터가 저장 된의 군/시를 이해 하는 것이 중요 이지만 Office 365와 함께 사용자 환경에서 데이터를 포함 하는 디스크에 직접 연결을 포함 하지 않습니다. (성능, 안정성 및 기타 중요 한 품질 특성 포함)는 Office 365를 통해 사용자 환경에는 전체로 확장 m i c 위치 수백 전세계는 고도로 분산 된 서비스 앞면 도어를 통해 연결을 해야 합니다. 대부분의 경우에서 최상의 사용자 환경이 중앙 위치 또는 지역에서 탈출 지점의 통해 Office 365에 연결 하는 것이 아니라 사용자 요청에 가장 가까운 Office 365 서비스 진입점을을 라우팅하도록 고객 네트워크를 허용 하 여 수행 합니다.
  
대부분의 고객에 대 한 Office 365 사용자는 여러 위치에 걸쳐 분산 됩니다. 최상의 결과 얻으려면이 문서에 설명 된 원칙 해야 적절할 수는 확장 (하지 수직) 관점에서 가장 가까운 지점의 Microsoft 글로벌 네트워크에서 현재 상태로, 지리적 위치를 하지 않도록 연결 최적화에 초점을 맞추고 Office 365 테 넌 트의 위치입니다. 사실, 즉, Office 365 테 넌 트 데이터를 특정 지리적 위치에 저장, 경우에 해당 테 넌 트에 대 한 Office 365 환경 분산 유지 되도록 닫기를 매우에 나타날 수 테 넌 트에 있는 모든 최종 사용자 위치에 근접 하 (네트워크) .
  
## <a name="office-365-connectivity-principles"></a>Office 365 연결 원칙
<a name="BKMK_Principles"> </a>

다음 원칙을 최적의 Office 365 연결 및 성능을 달성 하기 위해 사용 하는 것이 좋습니다. 이러한 Office 365 연결 원칙을 사용 하 여 사용자 트래픽을 관리 하 고 Office 365에 연결 하는 경우 최상의 성능을 얻으려면.
  
네트워크 디자인의 주요 목표는 Microsoft 글로벌 네트워크 대기 시간이 적은 Microsoft의 데이터 센터의 모든 상호 연결 하는 Microsoft의 공용 네트워크 백본에 네트워크에서 왕복 시간 (RTT)을 줄이면 대기 시간을 최소화 하기 위해 여야 합니다. 사서함과 클라우드 전세계에 분산 응용 프로그램 진입점입니다. Microsoft 글로벌 네트워크 [어떻게 Microsoft 구축 하는 신속 하 고 신뢰할 수 있는 전역 네트워크에](https://azure.microsoft.com/en-us/blog/how-microsoft-builds-its-fast-and-reliable-global-network/)대 한 자세한 내용을 알아보십시오.
  
### <a name="identify-and-differentiate-office-365-traffic"></a>식별 하 고 Office 365 트래픽을 구분합니다
<a name="BKMK_P1"> </a>

![Office 365 트래픽을 확인합니다](media/621aaec9-971d-4f19-907a-1ae2ef6d72fc.png)
  
일반 인터넷 바인딩 네트워크 트래픽으로부터 해당 트래픽을 구분할 수 없게 하는 첫번째 단계는 Office 365 네트워크 트래픽을 식별 합니다. 네트워크 경로 최적화, 방화벽 규칙, 브라우저 프록시 설정 및 특정 끝점에 대 한 네트워크 검사 장치의 바이패스와 같은 접근 방법의 조합을 구현 하 여 office 365 연결을 최적화할 수 있습니다.
  
이전 Office 365 최적화 지침 Office 365 끝점 범주로 구분할 두 **필수** 와 **선택**합니다. 끝점에 추가 된 새로운 Office 365 서비스 및 기능을 지원 하기 위해으로 Office 365 끝점을 다시 구성 되었습니다 세 범주에 있는 우리: **최적화**, **허용** 및 **기본값**입니다. 최적화를 보다 쉽게 이해 하 고 구현 하는 범주에 있는 모든 끝점에 각 범주에 대 한 지침이 적용 됩니다. 
  
Office 365 끝점 범주 및 최적화 방법에 대 한 자세한 내용은 [새 Office 365 끝점 범주](office-365-network-connectivity-principles.md#BKMK_Categories) 섹션을 참조 하십시오.
  
Microsoft는 이제 모든 Office 365 끝점을 웹 서비스로 게시 하 고이 데이터를 사용 하 여 최상의 방법에 대 한 지침을 제공 합니다. 반입 및 Office 365 끝점을 사용 하는 방법에 대 한 자세한 내용은 [Office 365 Url 및 IP 주소 범위는](https://support.office.com/en-us/article/office-365-urls-and-ip-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2?ui=en-US&amp;rs=en-US&amp;ad=US)문서를 참조 하십시오.
  
### <a name="egress-network-connections-locally"></a>로컬로 탈출 네트워크 연결
<a name="BKMK_P2"> </a>

![로컬로 탈출 네트워크 연결](media/b42a45be-1ab4-4073-a7dc-fbdfb4aedd24.png)
  
로컬 DNS 및 인터넷 탈출은 연결 대기 시간 감소 하 고 Office 365 서비스에 대 한 항목의 가장 가까운 지점에 대해 사용자 연결을 확인 하는 것에 대 한 중요 한 중요 합니다. 복잡 한 네트워크 토폴로지를 로컬 DNS 및 로컬 인터넷 송신 모두를 함께 구현 하는 것이 중요 됩니다. Office 365 항목의 가장 가까운 지점에 대 한 클라이언트 연결을 회람 하는 방법에 대 한 자세한 내용은 [클라이언트 연결](https://support.office.com/en-us/article/client-connectivity-4232abcf-4ae5-43aa-bfa1-9a078a99c78b)문서를 참조 하십시오.
  
Office 365 같은 클라우드 서비스 도입 하기 전에 최종 사용자의 네트워크 아키텍처 디자인 요인으로 인터넷을 통해 연결 된 비교적 간단 합니다. 인터넷 서비스 및 웹 사이트는 전세계 어디에서 배포 된, 하는 경우 회사 탈출 포인트와 모든 지정 된 대상 끝점 사이의 대기 시간 지리적 거리의 함수 대부분입니다.
  
기존 네트워크 아키텍처에서 모든 아웃 바운드 인터넷 연결 하는 회사 네트워크를 통과 및 송신 하는 중앙 위치에서 합니다. Microsoft의 클라우드 서비스가 성숙 과정을 따라 분산된 인터넷 네트워크 아키텍처는 되 고 대기 시간에 민감한 클라우드 서비스를 지원 하기 위한 중요 합니다. Microsoft 글로벌 네트워크 서비스 앞면 도어 분산 인프라를 가장 가까운 진입점에 들어오는 클라우드 서비스 연결을 라우팅하는 글로벌 진입점의 동적 fabric 대기 시간 요구 사항을 수용 하도록 설계 되었습니다. 이 "마지막 마일"의 길이 줄일 수 Microsoft 클라우드 고객 고객 및 클라우드 간의 경로 효과적으로 줄여 있습니다.
  
엔터프라이즈 Wan 보통 하나 이상의 프록시 서버를 통해 인터넷에 탈출 하기 전에 검사에는 중앙 회사 본사 backhaul 네트워크 트래픽을 만들어진 경우가 많습니다. 아래 다이어그램에서는 네트워크 토폴로지를 보여줍니다.
  
![기존 엔터프라이즈 네트워크 모델](media/fc87b8fd-a191-47a7-9704-1e445599813a.png)
  
Office 365 전세계 모든 프런트엔드 서버를 포함 하는 Microsoft 글로벌 네트워크에서 실행 되므로 자주 됩니다 사용자의 위치에 근접 한 프런트엔드 서버. 로컬 인터넷 탈출을 제공 하 고 Office 365 끝점에 대 한 로컬 이름 확인 기능을 제공 하는 내부 DNS 서버를 구성 하 여 Office 365에 대 한 향하는 네트워크 트래픽을 사용자에 게 최대한 가깝게 Office 365 프런트엔드 서버에 연결할 수 있습니다. 아래 다이어그램에 가장 가까운 Office 365 진입점을 가장 짧은 경로 따르는 것 본사, 지사 사무실 및 원격 위치에서 연결 하는 사용자를 허용 하는 네트워크 토폴로지 예를 보여줍니다.
  
![지역 탈출 포인트와 WAN 네트워크 모델](media/4d4c07cc-a928-42b8-9a54-6c3741380a33.png)
  
네트워크 경로 단축 Office 365에 이와 같은 방식으로 진입점 수 연결 성능을 개선 하 고 최종 사용자는 Office 365 경험 하 고도 도움말 이후 Office 365 성능에는 네트워크 구조 변경의 영향을 줄일 수 있습니다 및 안정성 합니다.
  
또한 DNS 요청 응답 하는 DNS 서버가 멀리 떨어져 있는 또는 사용 중인 경우 지연이 발생할 수 있습니다. 분기 위치에서 로컬 DNS 서버를 구축 하 고 캐시 DNS 레코드를 적절 하 게 구성 확인 하 여 이름 확인 대기 시간을 최소화할 수 있습니다.
  
최적의 연결 모델 항상 네트워크 탈출 회사 네트워크 또는 집, 호텔, 커피숍 등 원격 위치에 인지 여부에 관계 없이 사용자의 위치를 제공 하 여 것 지역 탈출 Office 365에 적합 한에서 작업할 수 있는 동안 및 공항 합니다. 이 로컬 직접 탈출 모델은 아래 다이어그램에 표시 됩니다.
  
![로컬 탈출 네트워크 아키텍처](media/6bc636b0-1234-4ceb-a45a-aadd1044b39c.png)
  
대기업용 Office 365 채택 하는 Office 365에 대 한 사용자 연결 가장 가까운 Microsoft 글로벌 네트워크 항목에 가능한 가장 짧은 경로 수행할 수 있도록 하 여 Microsoft 글로벌 네트워크 서비스 앞면 도어 분산 아키텍처의 기능을 사용할 수 있습니다. 지점입니다. 로컬 탈출 네트워크 아키텍처 사용자 위치에 관계 없이 가장 가까운 탈출을 통해 라우팅할 수에 대 한 Office 365 트래픽 허용 하 여이 작업을 수행 합니다.
  
로컬 탈출 아키텍처 전통적인 모델을 통해 다음과 같은 이점이 있습니다.
  
- 경로 길이 최적화 하 여 Office 365 성능을 최적화를 제공 합니다. 동적으로 서비스 앞면 도어 분산 인프라 하 여 최종 사용자 연결에 가장 가까운 Office 365 진입점으로 라우팅됩니다.
- 로컬 탈출 허용 하 여 회사 네트워크 인프라에서 부하를 줄입니다.
- 클라이언트 끝점 보안 및 클라우드 보안 기능을 활용 하 여 양쪽 끝에서 연결을 보호 합니다.

### <a name="avoid-network-hairpins"></a>네트워크 hairpins 방지
<a name="BKMK_P3"> </a>

![Hairpins 방지](media/ee53e8af-f57b-4292-a256-4f36733b263a.png)
  
일반으로 사용자와 가장 가까운 Office 365 끝점 사이의 가장 짧은, 최단 경로 최상의 성능을 제공 합니다. 다른 중간 위치 (예: 보안 스택의, 클라우드 기반 웹 게이트웨이 클라우드 액세스 브로커)를 먼저 리디렉션되면 특정 대상에 대 한 WAN 또는 VPN 트래픽이 바인딩된 때 발생 하는 네트워크 헤어핀 소개 (영문)에 대 한 잠재적 리디렉션 및 대기 시간을 지리적으로 멀리 떨어져 있는 끝점입니다. 네트워크 hairpins 라우팅 피어 링 비효율성 또는 최적화 되지 않은 (원격) DNS 조회 하 여도 발생할 수 있습니다.
  
Office 365 연결 로컬 탈출 경우에도 네트워크 hairpins에 따라 달라 집니다 아닌지 확인, 사용자 위치에 대 한 인터넷 탈출이 Microsoft 글로벌 네트워크에 직접 피어 링 관계를 제공 하는데 사용 되는 ISP 닫습니다 여부 확인 해당 위치에 근접 합니다. 신뢰할 수 있는 Office 365 트래픽을 직접 보내도록 라우팅 탈출을 구성 하려면, 인터넷 바인딩 트래픽을 처리 하는 프록시 또는 제 3 자 클라우드 또는 클라우드 기반 네트워크 보안 공급 업체를 통해 터널링 것과 반대로 합니다. Office 365 끝점의 로컬 DNS 이름 확인을 직접 라우팅 외에도 가장 가까운 Office 365 진입점 사용 중인 사용자 연결에 대 한 확인 하는데 도움이 됩니다.
  
클라우드 기반 네트워크 또는 Office 365 트래픽에 대 한 보안 서비스를 사용 하는 경우에 hairpinning 효과 평가 하 고 이해 하는 Office 365 성능에 미치는 영향을 확인 합니다. 이 수와 지사 및 Microsoft 글로벌 네트워크 피어 링 포인트, 품질의 네트워크 피어 링 관계의 수에 관계에 트래픽을 전달 되는 서비스 공급자 위치를 검사 하 여 수행할 수 있습니다. ISP에 문의 하 고 Microsoft, 및 backhauling 서비스 공급자 인프라에서의 성능에 영향을 사용 하 여 서비스 공급자입니다.
  
Office 365 진입점 및 최종 사용자에 게 자신의 근접 분산된 위치 많기 때문에 모든 제 3 자 네트워크 또는 보안 공급자에 게 Office 365 트래픽 라우팅에 미칠 수 부정적인 영향을 Office 365 연결 공급자 네트워크 없는 경우 최적의 Office 365 피어 링를 구성합니다.
  
### <a name="bypass-proxies-traffic-inspection-devices-and-duplicate-security-technologies"></a>바이패스 프록시, 트래픽 검사 장치 및 중복 된 보안 기술
<a name="BKMK_P4"> </a>

![바이패스 프록시, 트래픽 검사 장치 및 중복 된 보안 기술](media/0131930d-c6cb-4ae1-bbff-fe4cf6939a23.png)
  
엔터프라이즈 고객의 네트워크 보안을 검토 해야 하 고 Office 365를 위한 위험 감소 방법을 바운드 트래픽은 및 Office 365 보안 기능을 사용 하 여 자신의 킬에 대 한 의존도, 성능에 영향을 주는, 및 비용이 많이 드는 네트워크 보안을 줄일 수 Office 365 네트워크 트래픽에 대 한 기술입니다.
  
대부분의 기업 네트워크 프록시, SSL 검사, 패킷 검사 및 데이터 손실 방지 시스템와 같은 기술을 사용 하 여 인터넷 트래픽에 대 한 네트워크 보안을 강화 합니다. 이러한 기술을 일반 인터넷 요청에 대 한 중요 한 위험 완화를 제공 하지만 성능, 확장성 및 Office 365 끝점에 적용 하면 최종 사용자 경험의 품질을 대폭 절감할 수 있습니다.
  
#### <a name="office-365-endpoints-web-service"></a>Office 365 끝점 웹 서비스
<a name="BKMK_WebSvc"> </a>

Office 365 관리자 스크립트를 사용 하 여 또는 끝점을 Office 365 끝점에서 구조적된 목록 사용 (영문)를 호출할 때 REST 웹 서비스를 경계 방화벽 구성과 다른 네트워크 장치를 업데이트 합니다. 이렇게 하면 Office 365에 대 한 바운드 트래픽을 식별, 적절 하 게 처리 이며 있는지 일반적이 고 자주 알 수 없는 인터넷 웹사이트에 대 한 바운드 네트워크 트래픽으로부터 다른 방법으로 관리 합니다. 웹 서비스에는 Office 365 끝점을 사용 하는 방법에 대 한 자세한 내용은 [Office 365 Url 및 IP 주소 범위는](https://support.office.com/en-us/article/office-365-urls-and-ip-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2?ui=en-US&amp;rs=en-US&amp;ad=US)문서를 참조 하십시오.
  
#### <a name="pac-proxy-automatic-configuration-scripts"></a>PAC (프록시 자동 구성) 스크립트
<a name="BKMK_WebSvc"> </a>

Office 365 관리자는 WPAD 또는 GPO를 통해 사용자 컴퓨터에 전달할 수 PAC (프록시 자동 구성) 스크립트를 만들 수 있습니다. 회사 네트워크를 통과 하는 것이 아니라 직접 인터넷 연결을 사용 하 여 Office 365 트래픽을 허용, WAN 또는 VPN 사용자에 게 Office 365 요청에 대 한 프록시를 무시 하도록 PAC 스크립트를 사용할 수 있습니다.
  
#### <a name="office-365-security-features"></a>Office 365 보안 기능
<a name="BKMK_WebSvc"> </a>

Microsoft는 데이터 센터 보안, 운영 보안 및 Office 365 서버와 자신이 표시 하는 네트워크 끝점 주위 위험 감소 하는 방법에 대 한 투명 하 게 합니다. 데이터 손실 방지, 바이러스 백신, 다단계 인증, 고객 잠금 상자, 고급 위협 보호, Office 365 위협 인텔리전스, Office 365 보안 네트워크 보안 위험을 줄이기 위한 사용할 수 있는 office 365 기본 제공 보안 기능 점수, Exchange Online Protection 및 네트워크 DDOS 보안 합니다.
  
Microsoft 데이터 센터 및 전역 네트워크 보안에 대 한 자세한 내용은 [Microsoft 보안 센터](https://www.microsoft.com/en-us/trustcenter/security)를 참조 하십시오.
  
## <a name="new-office-365-endpoint-categories"></a>새로운 Office 365 끝점 범주
<a name="BKMK_Categories"> </a>

Office 365 끝점은 네트워크 주소 및 서브넷의 다양 한 집합을 나타냅니다. 끝점 Url, 수 IP 주소 또는 IP 범위, 및 일부 끝점 특정 TCP/UDP 포트와 함께 나열 됩니다. Url *account.office.net* 같은 FQDN 수 또는 와일드 카드 URL like * \*. office365.com*합니다.
  
> [!NOTE]
> 네트워크 내에서 Office 365 끝점의 위치는 Office 365 테 넌 트 데이터의 위치를 직접 관련이 없습니다. 이러한 이유로 고객 분산 되 고 전역 서비스로 Office 365에서은 다음과 같아야 하 고 지리적 기준에 따라 Office 365 끝점에 대 한 네트워크 연결을 차단 하지 않아야 합니다.
  
Office 365 트래픽을 관리 하기 위한 사용해 이전 지침을에서 끝점을 된 범주로 구성 두, **필수** 와 **선택**합니다. 각 범주 내의 끝점을 필요한 서비스의 중요성에 따라 다른 최적화 하 고 Office 365 Url 및 IP 주소의 전체 목록은을 동일한 네트워크 최적화의 응용 프로그램의 당위성에 다 수의 고객에 직면 합니다. 
  
새 모델 끝점 **최적화**, **필수** 및 **기본**, 우선순위 기반 피벗 최상의 성능 향상을 실현 하는 데 네트워크 최적화 노력을 집중을 위치를 제공 하 세 범주에 분리 되 고 투자 수익률을 반환 합니다. 끝점은 시나리오의 네트워크 품질, 볼륨 및 성능을 봉투 및 구현의 용이성 유효 사용자 경험의 우편물 종류에 따라 위의 범주에 통합 됩니다. 지정된 된 범주에 대 한 모든 끝점에 동일한 방식으로 권장된 최적화를 적용할 수 있습니다.
  
- 모든 Office 365 서비스에 대 한 연결에 대 한 필요 하 고 넘는 Office 365 대역폭, 연결 및 데이터 볼륨의 75%를 차지 하는 끝점을 **최적화** 합니다. 이러한 끝점 네트워크 성능, 대기 시간 및 가용성을 가장 중요 한 되는 Office 365 시나리오를 나타냅니다. 모든 끝점 Microsoft 데이터 센터에서 호스팅됩니다. 이 종류의 끝점을 변경 하는 횟수 다른 두 종류의 끝점에 대 한 보다 훨씬 더 낮은 것으로 예상 됩니다. 이 범주에는 (~ 10)의 순서에 매우 작은 Url 및 IP 서브넷의 정의 된 집합 비즈니스 온라인 및 팀이 Microsoft Exchange Online, SharePoint Online, Skype와 같은 핵심 Office 365 작업을 하기 위한 전용 키 집합을 포함 합니다.

    압축 된 잘 정의 된 중요 한 끝점 목록을 계획 하 고 더 빠르고 쉽게 이러한 대상에 대 한 검색에 유용한 네트워크 최적화를 구현 하는데 도움이 됩니다.

    *최적화* 끝점의 예로 *https://outlook.office365.com* , *https://\<테 넌 트\>. sharepoint.com* 및 *https://\<테 넌 트\>-my.sharepoint.com* 합니다.

    최적화 방법은 다음과 같습니다.

  - 네트워크 장치 및 트래픽 가로채기, SSL 암호 해독, 패킷 검사 및 콘텐츠 필터링을 수행 하는 서비스에 *최적화* 끝점 바이패스 또는 허용 목록입니다.
  - 온-프레미스 프록시 장치 및 일반 인터넷 검색에 대 한 일반적으로 사용 하는 프록시 클라우드 기반 서비스를 무시 합니다.
  - 네트워크 인프라 및 경계 시스템 하 여 완전히 신뢰할 수 있는으로 이러한 끝점의 평가 우선순위를 지정 합니다.
  - 감소 또는 제거, WAN backhauling 매기고 사용자/지사 최대한 가깝게 이러한 끝점에 대 한 직접 분산된 인터넷 기반 탈출을 용이 하 게 합니다.
  - VPN 사용자에 대 한 이러한 클라우드 끝점에 대 한 직접 연결을 용이 하 게 분할 터널링를 구현 하 여 합니다.
  - DNS 이름 확인 하 여 반환 된 IP 주소에 이러한 끝점에 대 한 라우팅 탈출 경로 일치 하는지 확인 합니다.
  - Microsoft 글로벌 네트워크의 가장 가까운 인터넷 피어 링 지점에 직접, 최소한의 대기 시간 라우팅에 대 한 SD WAN 통합에 대 한 이러한 끝점 우선순위를 지정 합니다.

- 끝점을 **허용** 특정 Office 365 서비스 및 기능에 대 한 연결에 필요 하지만 네트워크 성능 및 *최적화* 범주에 나타난 대기 시간에 민감한 같이 하지 않습니다. 대역폭 및 연결 수의 관점에서 볼 때 이러한 끝점의 전체 네트워크 공간이 훨씬 더 작은 이기도합니다. 이러한 끝점 Office 365 전용 및 Microsoft 데이터 센터에서 호스팅됩니다. 다양 한 Office 365 마이크로-서비스 및 의존 관계 (~ 100 Url)의 순서를 나타내는 있으며 *최적화* 범주에 있는 것 보다 더 높은 속도로 변경으로 예상 됩니다. 이 범주에 있는 모든 끝점 정의 된 전용된 IP 서브넷에 연결 됩니다.

    *허용* 끝점에 대 한 네트워크 최적화에는 Office 365 사용자 환경을 향상 시킬 수 있지만 일부 고객이 자신의 네트워크에 대 한 변경 내용을 최소화 하기 위해 구체적으로 더 많은 최적화 이러한 범위 하도록 선택할 수 있습니다.

    *허용* 끝점의 예로 *https://\*. protection.outlook.com* 및 *https://accounts.accesscontrol.windows.net*합니다.

    최적화 방법은 다음과 같습니다.

  - 네트워크 장치 및 트래픽 가로채기, SSL 암호 해독, 패킷 검사 및 콘텐츠 필터링을 수행 하는 서비스에서 *허용* 끝점 바이패스 또는 허용 목록입니다.
  - 네트워크 인프라 및 경계 시스템 하 여 완전히 신뢰할 수 있는으로 이러한 끝점의 평가 우선순위를 지정 합니다.
  - 감소 또는 제거, WAN backhauling 매기고 사용자/지사 최대한 가깝게 이러한 끝점에 대 한 직접 분산된 인터넷 기반 탈출을 용이 하 게 합니다.
  - DNS 이름 확인 하 여 반환 된 IP 주소에 이러한 끝점에 대 한 라우팅 탈출 경로 일치 하는지 확인 합니다.
  - Microsoft 글로벌 네트워크의 가장 가까운 인터넷 피어 링 지점에 직접, 최소한의 대기 시간 라우팅에 대 한 SD WAN 통합에 대 한 이러한 끝점 우선순위를 지정 합니다.

- **기본** 끝점 Office 365 서비스 및 모든 최적화 필요 하지 않으며 표준 인터넷 바운드 트래픽을으로 고객 네트워크 취급 될 수 있습니다는 종속 항목을 나타냅니다. 참고가이 범주에 있는 일부 끝점을 Microsoft 데이터 센터에서 호스팅될 수 있습니다. 예로 *https://odc.officeapps.live.com* 및 *https://appexsin.stb.s-msn.com*합니다.

Office 365 네트워크 최적화 방법에 대 한 자세한 내용은 [Office 365 관리 끝점](https://support.office.com/en-us/article/managing-office-365-endpoints-99cab9d4-ef59-4207-9f2b-3728eb46bf9a#ID0EAEAAA=0._Overview)문서를 참조 합니다.
  
## <a name="comparing-network-perimeter-security-with-endpoint-security"></a>끝점 보안이 포함 된 네트워크 경계 보안 비교 (영문)
<a name="BKMK_SecurityComparison"> </a>

기존 네트워크 보안의 목표 침입 및 악의적인 이용에 대 한 회사 네트워크 경계를 강화 하는 것입니다. Office 365를 채택 하는 조직,으로 일부 네트워크 서비스 및 데이터는 완전히 또는 부분적으로 클라우드로 마이그레이션 합니다. 네트워크 아키텍처에 어떠한 기본 변경와 마찬가지로,이 프로세스는 새로운 요소를 고려 하는 네트워크 유가 증권의 재계산이 필요 합니다.
  
- 클라우드 서비스 채택 하는 네트워크 서비스 및 데이터 온-프레미스 데이터 센터와 클라우드 간에 배포 및 경계 보안은 자체적으로 적절 한 나타나지 않습니다.
- 원격 사용자의 홈으로 지정, 호텔 커피숍 등 제어 되지 않은 위치에서 클라우드에서 및 온-프레미스 데이터 센터에서 회사 리소스에 연결합니다.
- 특정 용도의 보안 기능 점점 기본 클라우드 서비스 제공 하 고 잠재적으로 보충 하거나 바꿀 수 있습니다 기존 보안 시스템입니다.

Microsoft는 전체 범위의 Office 365 보안 기능을 제공 하 고 Office 365에 대 한 데이터 및 네트워크 보안을 보장 하는데 도움이 되는 보안 모범 사례를 적용 하는 것에 대 한 지침을 제공 합니다. 권장된 모범 사례는 다음과 같습니다.
  
- **다단계 인증 사용 (MFA)** MFA는 사용자를 전화 통화, 텍스트 메시지 또는 올바르게 자신의 암호를 입력 한 후 스마트 전화기에서 전자 app 알림을 확인을 요구 하 여 강력한 암호 전략에 추가 계층의 보호를 추가 합니다.

- **Office 365 클라우드 앱 보안 사용** 비정상적인 활동을 추적 하 고 그에 작용 하는 정책을 설정 합니다. 로그인 시도가 실패 한 여러 관리자가 많은 양의 데이터를 다운로드 하는 등의 비정상 또는 위험한 사용자 작업을 검토할 수 있도록 Office 365 클라우드 응용 프로그램 보안 경고를 설정 또는 연결 알 수 없거나 위험한 ip에서 주소입니다.

- **데이터 손실 방지 (DLP) 구성** DLP를 사용 하면 중요 한 데이터를 식별 하 고 사용자가 실수로 또는 의도적으로 데이터를 공유 하는 것을 방지 하는 정책을 만들 수 있습니다. DLP은 사용자에 게 잃지 규격 유지할 수 있도록 Exchange Online, SharePoint Online 및 OneDrive를 포함 하 여 Office 365에서 작동 합니다.

- **사용 하 여 고객 Lockbox** Office 365 관리자를으로 Microsoft 기술 지원 엔지니어 도움말 세션 중에 데이터에 액세스 하는 방법을 제어 하려면 고객 Lockbox를 사용할 수 있습니다. 엔지니어가 문제를 해결 하 고 문제를 해결 하 여 데이터에 대 한 액세스를 필요로 하는의 경우, 고객 Lockbox를 사용 하면 승인 하거나 거부 하는 액세스 요청 수 있습니다.

- **Office 365 보안 점수를 사용 하 여** 보안 점수는 할 수 있는 추가 위험을 줄이는 것을 권장 하는 보안 분석 도구입니다. 보안 점수 Office 365 설정 및 작업을 확인 하 고 Microsoft에 의해 설정 된 초기 계획을 비교 합니다. 최상의 보안 방법으로는 어떻게 정렬 기준으로 점수를 얻을 수 있습니다.

향상 된 보안 전체적인 접근 방식을 고려 사항은 다음을 포함 해야 합니다.
  
- 클라우드 기반을 적용 하 여 끝점 보안 및 Office 클라이언트 보안 기능으로 경계 보안에서 강조를 이동 합니다.
  - 데이터 센터에 보안 경계를 축소
  - 사무실 내부 또는 원격 위치에서 사용자 장치에 대 한 해당 하는 트러스트를 사용 하도록 설정
  - 데이터 위치 및 사용자 위치 보호 중점적으로 고려할
  - 관리 되는 사용자 컴퓨터에 더 높은 트러스트 끝점 보안을
- 모든 정보 보안을 전체적으로 관리 하 여 하지는 경계에만 초점을 맞추고
  - WAN 및 신뢰할 수 있는 트래픽을 보안 장치를 무시 하도록 허용 하 고 게스트 Wi-fi 네트워크를 관리 되지않는 장치를 분리 하 여 경계 네트워크 보안 만들기 (영문)를 재정의 합니다.
  - 회사 WAN 지의 네트워크 보안 요구 사항 감소
  - 일부 네트워크 경계 보안 장치 방화벽 여전히 필요 하지만 로드와 같은 감소
  - Office 365 트래픽에 대 한 로컬 탈출 보장
- 향상 된 [증분 최적화](office-365-network-connectivity-principles.md#BKMK_IncOpt) 섹션의 설명에 따라 점진적으로 해결할 수 있습니다. 일부 최적화 기술은 네트워크 아키텍처에 따라 더 나은 비용/혜택 비율을 제공할 수 있습니다 하 고 조직에 가장 적합 한를 구성 하는 최적화를 선택 해야 합니다.

Office 365 보안 및 규정 준수에 대 한 자세한 내용은 [Office 365의 규정 준수 및 보안 개요 (영문)](https://support.office.com/en-us/article/overview-of-security-and-compliance-in-office-365-dcb83b2c-ac66-4ced-925d-50eb9698a0b2?ui=en-US&amp;rs=en-US&amp;ad=US)문서를 참조 합니다.
  
## <a name="incremental-optimization"></a>증분 최적화
<a name="BKMK_IncOpt"> </a>

이 문서 앞부분의 SaaS에 대 한 이상적인 네트워크 연결 모델을 나타내는는 하지만 획기적인 복잡 한 네트워크 아키텍처와 많은 대규모 조직에 대 한가 되지는 직접 이러한 모든 변화를 확인 하기에 적합 합니다. 이 섹션에서는 Office 365 성능 및 안정성 향상 시키는데 도움이 되는 증분 변경 횟수에 설명 합니다.
  
Office 365 트래픽을 최적화 하는데 사용할 방법을 네트워크 토폴로지 및 구현 하는 네트워크 장치에 따라 달라 집니다. 다양 한 위치 및 복잡 한 네트워크 보안 사례와 대기업 전체 또는 대부분 소규모 조직 수만 하는 동안 [Office 365 연결 원칙](office-365-network-connectivity-principles.md#BKMK_Principles) 섹션에 나열 된 원칙을 포함 하는 전략을 개발 해야 합니다. 하나 또는 두 고려해 야 합니다.
  
표시 된 순서 대로 각 메서드를 적용 한 증분 프로세스로 최적화에 접근할 수 있는 있습니다. 다음 표에 사용자의 최대 수에 대 한 대기 시간 및 안정성에 대 한 영향의 순서에 중요 한 최적화 방법입니다.
  
|**최적화 메서드**|**설명**|**영향**|
|:-----|:-----|:-----|
|로컬 DNS 확인 및 인터넷 송신  <br/> |각 위치에서 로컬 DNS 서버를 구축 하 고 사용자의 위치에 최대한 가깝게 인터넷에는 Office 365 연결 탈출을 확인 합니다.  <br/> | 대기 시간 최소화  <br/>  가장 가까운 Office 365 진입점에 대 한 신뢰할 수 있는 연결을 향상  <br/> |
|지역 탈출 포인트를 추가 합니다.  <br/> |회사 네트워크에 하나만 탈출 지점의 하지만 여러 위치를 하는 경우 사용자가 가장 가까운 Office 365 진입점에 연결할 수 있도록 탈출 지역 포인트를 추가 합니다.  <br/> | 대기 시간 최소화  <br/>  가장 가까운 Office 365 진입점에 대 한 신뢰할 수 있는 연결을 향상  <br/> |
|바이패스 프록시와 검사 장치  <br/> |탈출 포인트를 직접 Office 365 요청을 보내는 PAC 파일을 사용 하 여 브라우저를 구성 합니다.  <br/> 에 지 라우터 및 검사 하지 않고 Office 365 트래픽을 허용 하도록 방화벽을 구성 합니다.  <br/> | 대기 시간 최소화  <br/>  네트워크 장치에서 부하를 감소  <br/> |
|VPN 사용자에 대 한 직접 연결을 사용 하도록 설정  <br/> |VPN 사용자에 대 한 분할 터널링를 구현 하 여 사용자의 네트워크에서 직접 아니라 VPN 터널을 통해 연결에 대 한 Office 365 연결을 사용 하도록 설정 합니다.  <br/> | 대기 시간 최소화  <br/>  가장 가까운 Office 365 진입점에 대 한 신뢰할 수 있는 연결을 향상  <br/> |
|SD WAN 전통적인 WAN에서 마이그레이션  <br/> |SD-Wan (소프트웨어에 정의 된 Wide Area Network) WAN 관리를 단순화 하 고 가상 기기, Vm (가상 컴퓨터)를 사용 하 여 compute 리소스의 가상화 비슷합니다 전통적인 WAN 라우터 교체 하 여 성능을 향상 시킬.  <br/> | 성능 및 WAN 트래픽 관리 효율성 향상  <br/>  네트워크 장치에서 부하를 감소  <br/> |