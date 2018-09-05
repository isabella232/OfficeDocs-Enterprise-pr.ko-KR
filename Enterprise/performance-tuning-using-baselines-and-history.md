---
title: 초기 계획 및 성능 기록을 사용하여 Office 365 성능 조정
ms.author: tracyp
author: MSFTTracyP
manager: laurawi
ms.date: 8/31/2017
ms.audience: Admin
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: 1492cb94-bd62-43e6-b8d0-2a61ed88ebae
description: Office 365와 사용자 연결의 대략적인 기준선을 설정할 수 있는 비즈니스 간의 연결 성능을 확인 하는 간단한 방법과 있습니다. 클라이언트의 성능 기록 컴퓨터 연결 알면 초기 새로 등장 문제를 검색 하 고 식별 하 고, 문제를 예측 하 하는 데 도움이 수 있습니다.
ms.openlocfilehash: bb1fe1e1450798e43c15a07610e27450bce6ea5b
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/27/2018
ms.locfileid: "22542067"
---
# <a name="office-365-performance-tuning-using-baselines-and-performance-history"></a>초기 계획 및 성능 기록을 사용하여 Office 365 성능 조정

Office 365와 사용자 연결의 대략적인 기준선을 설정할 수 있는 비즈니스 간의 연결 성능을 확인 하는 간단한 방법과 있습니다. 클라이언트의 성능 기록 컴퓨터 연결 알면 초기 새로 등장 문제를 검색 하 고 식별 하 고, 문제를 예측 하 하는 데 도움이 수 있습니다.
  
(영문) 성능 문제에 사용 했던,이 문서를 어떻게 알 수 있을까요 특정인 중인 문제는 성능 문제 및 Office 365 서비스 인시던트 하지와 동일 하 게 관련 된 일반적인 질문을 고려 하는 데 도움이 하도록 되어 있습니까? 성능 향상을 위해 방법을 계획할 수 장기간? 성능에 눈을 유지할 수는 방법 팀 또는 클라이언트는 Office 365를 사용 하는 동안 성능이 저하 표시 되는지를 하는 경우 이러한 질문에 대 한 잘 모르십니까에서 읽습니다.
  
> [!IMPORTANT]
> **클라이언트와 Office 365 간의 성능 문제를 지금 바로?** [성능 문제를 해결 Office 365에 대 한 계획](performance-troubleshooting-plan.md)에 설명 된 단계를 수행 합니다. 
    
## <a name="something-you-should-know-about-office-365-performance"></a>Office 365 성능에 대해 알고 있어야 자료

Office 365를 호스팅하면 자동화, 되지만 실제 사용자만이 아니라 지속적으로 모니터링 하는 고용량, 전용 Microsoft 네트워크 내 개체가 존재 합니다. Office 365 클라우드를 유지 관리 역할의 부분은 건물의 성능 조정 및 것이 가능한 간소화 합니다. Office 365 클라우드의 클라이언트를 인터넷을 통해 연결 하는 이므로 너무 Office 365 서비스 간에 성능을 미세 조정 하는 연속 노력 합니다. 성능 향상을 클라우드에 거 중지 이며 정상적이 고 빠른 클라우드를 유지 하는 누적된 경험이 많은 합니다. 현재 위치에서 Office 365에 연결 하는 성능 문제가 발생 하면 가장 좋은 시작 하 아니며 지원 사례에서 대기 합니다. 대신, '는 inside out (영문) '에서 문제를 조사 시작 해야 합니다. 즉, 내부 네트워크에서 시작 하 고 Office 365로 작업을 진행 합니다. Office 365 지원 사례를 열기 전에 데이터를 수집할 수 있으며를 탐색 하 고 문제를 해결할 수, 작업을 수행할 수 있습니다.
  
> [!IMPORTANT]
> 용량 계획 및 Office 365의 제한에 유의 합니다. 해당 정보는 성능 문제를 해결 하려고 할 때 곡선 앞 하면 배치 됩니다. [Office 365 플랫폼 서비스 설명](https://technet.microsoft.com/en-us/library/office-365-service-descriptions.aspx)에 대 한 링크는 다음과 같습니다. 중앙 허브를 이며 Office 365에서 제공 하는 모든 서비스 여기에서 자신의 서비스 설명에 대 한 이동 하는 링크를 포함 합니다. 즉, 필요한 경우 표준 제한 SharePoint Online에 대 한 참조를 등 [SharePoint Online 서비스 설명](https://technet.microsoft.com/en-us/library/sharepoint-online-service-description.aspx) 을 클릭 하는 해당 [SharePoint Online 제한 섹션](https://go.microsoft.com/fwlink/p/?LinkID=856113)을 찾습니다. 
  
이해 하는 문제 해결로 이동 되었는지 확인 성능 까지의 슬라이드 지는 이상적인된 값을 확보 하 고 영구적으로 유지 관리 하는 방법에 대 한 없는 (,이 다음 필요에 따른 고대역폭 작업 같은 온 보 딩 생각 되는 경우는 많은 수의 사용자를 매우 덜어줍니다 수-수 있으므로 수행 계획 성능에 미치는 영향에 대 한 다음 큰 데이터 마이그레이션을 수행 하는 또는). 수 있고을 대략적으로 성능 목표를가지고 있어야 하 고, 하지만 변수 재생 성능, 따라서 성능에 많은 달라 집니다. 이것은 성능 특성입니다. 
  
특정 목표를 충족 하는 방법에 대 한 되어있지 성능 문제를 해결 하 고 이러한 번호에 무기한 유지 하는 것이 모든 변수를 지정 된 기존 작업을 개선 하는 방법에 대 한 합니다. 
  
## <a name="okay-what-does-a-performance-problem-look-like"></a>자, 성능 문제가 무엇입니까?

첫째, 발생 하는 무엇 인지 실제로 성능 문제 및 서비스 문제를 하지 있는지 확인 해야 합니다. 성능 문제는 Office 365에서 서비스 사고와에서 다릅니다. 다음은 구분 알려주어야 하는 방법입니다.
  
Office 365 서비스는 문제가 있을 경우 문제가 발생 한 서비스입니다. Office 365 관리 센터에서 **현재 상태** 따라 빨간색 또는 노란색 아이콘 표시, Office 365에 연결 하는 클라이언트 컴퓨터에서 성능이 저하 될 수도 있습니다. 예, 빨간색 아이콘을 보고 하는 현재 상태 옆에 있는 Exchange **Investigating** 참조 하는 경우 받을 수 있습니다 다음도 통화 묶음 Exchange Online을 사용 하는 클라이언트 사서함 잘못 수행 하는 불만 제기 하는 조직에 있는 사람이 보낸. 경우에 Exchange Online 성적 방금 변경 되었습니다. 인 한 피해 서비스 내에서 문제를 가정할 수는 있습니다. 
  
![서비스 복원를 표시 하는 Exchange를 제외 하 고 녹색를 표시 하는 모든 작업 부하와 Office 365 상태 대시보드 합니다.](media/ec7f0325-9e61-4e1a-bec0-64b87f4469be.PNG)
  
이 시점, Office 365 관리자 확인 하 여 **현재 상태** 및 다음 **세부 정보 보기 및 내용**, 자주, 시스템에서 수행 하는 유지 관리를 최신 상태로 유지 하기 위해서는. **현재 상태** 대시보드, 변경 사항 및 서비스의 문제에 대 한 업데이트 되었습니다. 메모 및 상태 기록, 관리자가 관리자를 기록 하는 설명이 있습니까에 영향을 평가할 수 있도록 하 고 진행 중인 작업에 대 한 게시 하면 유지 합니다. 
  
![그림은 Office 365 상태 대시보드 설명 하는 Exchange Online 서비스 복원 되 고 이유입니다.](media/66609554-426a-4448-8be6-ea09817f41ba.PNG)
  
성능 문제 사고 성능이 저하 될 수 있는 경우에 문제가 발생 한 서비스를 없습니다. 성능 문제는 다음과 같습니다.
  
- 서비스에 대 한 보고 하는 Office 365 관리 센터 **현재 상태** 는 관계 없이 성능 문제가 발생 합니다. 
    
-  비교적 원활 하 게 수행 되어야 하는 데 사용 되는 문제를 완료 하려면 시간이 오래 걸립니다 또는 완료 되지 않습니다. 
    
- 너무, 문제를 복제할 수 또는 적어도 알고 있는 오른쪽 일련의 단계를 수행 하는 경우에 것입니다.
    
-  문제가 간헐적으로 있으면는 여전히 패턴, 등 알고 있는 오전 10 시 하 여 해야 함을 사용자에 게 Office 365를 안전 하 게 액세스할 수 없는 호출 하 고 정오로 주위 호출 하 여 소멸 됩니다. 
    
이 잠재적인 익숙한 사용자입니다. 친숙 한 너무 엔터프라이즈 무선 전화 통신 합니다. 성능 문제를 알고 있으면 질문 되 면 "어떻게 할까요 다음?" 이 문서의 나머지 부분에 정확 하 게 하는 결정 하는데 도움이 됩니다.
  
## <a name="how-to-define-and-test-the-performance-problem"></a>정의 하 고 성능 문제를 테스트 하는 방법

성능 문제는 종종 시간이 지남에 따라 등장 실제 문제를 정의 하는 복잡 한 될 수 있도록 합니다. 좋은 문제 문과 문제 컨텍스트의 상태 이기만 하면 만들어야 하며 다음 해야 테스트 단계를 반복 하는 일을 win 합니다. 그렇지 않은 경우 사용자가 직접 없음 오류를 통해 경우 손실 될 수 있습니다. 이유는 무엇입니까? 물론 충분 한 정보를 제공 하지 않는 문제 명령문에 대 한 예가 사항은 다음과 같습니다.
  
- 알 수 하지 않았으므로, 자료를 사용 하 고 내 일정을 내 받은 편지함에서 전환을 않으며 이제 coffee 나누기를. 하기가 더에 사용 되는 것 처럼 작동 합니까?
    
- 계속 수행 됨을 SharePoint Online 내 파일을 업로드 합니다. 이유는 것은 오후 하지만 다른 시간에 느린는 빠른? 수 없는 방금 수 빠른 있습니까?
    
위의 문제가 있는 명령문에 의해 야기 되는 여러 큰 과제 있습니다. 특히, 내용을 처리할 명확 하지 않은 많습니다. 예를 들어:
  
- 명확 하지 않기 받은 편지함과 일정으로 전환할 사용 하는 방법을 랩톱 작업을 수행 합니다.
    
- 사용자 표시 되 면 "없습니다 방금 것이 fast", "빠른" 이란?
    
- 얼마나 오래 "무제한" 인? 여러 한지 또는 분, 초, 또는 수 사용자 lunch 이동한 후 사용자를 반환 하는 후 10 분을 완료 합니다?
    
이 모든 관리 및 문제 해결사에서 다음과 같은 문제가 있는 명령문에서 다양 한 세부 정보를 인식을 사용할 수 없습니다 고려 하지 않고 됩니다. 예: 문제가 발생 하 고, 시작 하는 경우 사용자만 전혀 및 집에서 작동 하는지 볼 수는 홈 네트워크;에서 작업 하는 동안 저속 전환 사용자 로컬 클라이언트 또는 사용자에 여러 다른 RAM 위주의 응용 프로그램을 실행 해야 기존 운영 체제를 실행 하는 또는 최근 업데이트를 실행 하지 않은 합니다.
  
사용자가 성능 문제를 보고 때 많은 정보를 수집 합니다. 이 정보를 수집 하는 일부 문제, 범위 또는 조사 하 라고 하는 프로세스입니다. 다음은 기본 범위 목록 성능 문제에 대 한 정보를 수집 하는데 사용할 수 있습니다. 이 목록은, 완전 하지는 이지만 직접 중 하나를 시작 하는 위치: 
  
- 어떤 날짜에 문제가 발생, 그리고 낮 또는 밤의 시간 되었습니까?
    
- 클라이언트 컴퓨터의 종류를 사용 하면 사용한, 및 어떻게에 연결 되며 비즈니스 네트워크 (VPN, 유선, 무선)?
    
- 원격으로 작업 중인 또는 사무실 하면가?
    
- 않은 다른 컴퓨터에서 동일한 작업을 수행 하 고 동일 하 게 동작 참조?
    
- 제공 하려는 경우는 문제가 아래로 취할 조치를 작성할 수 있도록 하는 단계를 안내 합니다.
    
- 몇 초 또는 시간 (분)에 느린 성능 이란?
    
- 전세계에는 하면 어디에 있습니까?
    
위이 질문 중 일부는 다른 사용자 보다 보다 명확 하 게 합니다. 대부분의 모든 문제 해결사 필요한 문제를 재현 하는 정확한 단계 이해 하 게 합니다. 따라서, else 수 문제점을 기록 하는 방법을 하는 다른 방법의 문제는 해결 하는 경우를 테스트할? 덜 분명 한 사항은 다음과 같이 "어떤 한 날짜 및 시간 않은 경우 문제를 참조?", "세계에서가 있는 경우?", 동시에 사용할 수 있는 정보 및 합니다. 사용자가 작업 하는 경우에 따라 유지 관리 이미 진행 중인 회사 네트워크의 부분에 시간 차이의 몇 시간 의미할 수 있습니다. 예: 회사에 하이브리드 SharePoint 검색을 쿼리할 수 있는 다음과 같은 있는 하이브리드 구현 하는 경우 2013 인스턴스 SharePoint Online 및 온-프레미스 SharePoint 서버를 모두에서 검색 인덱스, 업데이트 온-프레미스 팜에 진행 될 수 있습니다. 회사는 클라우드 모두에 있으면 추가 또는 제거 네트워크 하드웨어, DNS, 또는 기타 핵심 인프라에 회사 차원의 또는 하 변경 내용이 업데이트 롤아웃 시스템 유지 관리 포함 될 수 있습니다.
  
성능 문제를 해결 하는 경우 것과 같습니다 좀더 범죄 장면, 정확 하 게 하 고 증거에서 모든 결론을 그릴 observant 되도록 해야 합니다. 이 작업을 수행 하기 위해 좋은 문제가 발생 하는 문이 증거를 수집 하 여 가져와야 합니다. 컴퓨터의 상황에 맞는, 문제가 시작 된 경우 사용자의 컨텍스트 및 성능 문제를 노출 하는 정확한 단계를 포함 해야 합니다. 이 문제 설명 수, 하 고 노트의 가장 위쪽에 있는 페이지를 유지 해야 합니다. 해상도에 작업 한 후에 다시 문제 설명을 살펴보는 방법으로 테스트 하 고 작업을 수행할 문제를 해결 한 있는지 여부를 증명 하는 단계를 수행는 있습니다. 이것은 알면, 사용자 작업을 수행 하는 경우에 중요 합니다.
  
## <a name="do-you-know-how-performance-used-to-look-when-it-was-good"></a>성능 좋은 되었을 때 사용 하는 방법을 알고 있습니까?

운이 모르는 경우 다음 작업을 알 수 아무도 합니다. 아무도 번호 했습니다. 즉, "에 대 한 얼마나 많은 시간 (초) 했을 것 Office 365의에서 받은 편지함을 표시 하기 위해 수행 하는 데 사용 하 시겠습니까?" 또는 "기간 했을 것 중역 Lync 온라인 회의 있을 때 수행 하는 데 사용 하 시겠습니까?" 간단한 질문에 대답할 수 아무도 많은 기업 들에 대 한 일반적인 시나리오입니다.
  
누락 된 이란 성능 기준선 다음과 같습니다.
  
기준선에 성능에 대 한 컨텍스트를 제공합니다. 취해야 초기 계획을 필요에 따라 자주, 회사의 요구 사항에 따라 합니다. 더 큰 회사의 경우 작업 팀 온-프레미스 환경에 대 한 초기 계획 이미 걸릴 수 있습니다. 예, 세번째 월요일에 모든 SharePoint 서버 및 해당 월의 첫째 월요일에 모든 Exchange 서버 패치를 적용 하는 경우 작업 팀 작업의 목록을 있으며 실행는 중요 한 기능은 증명 하기 위해 사후 패치 시나리오 작동 합니다. 예, 받은 편지함, 보내기/받기를 클릭 하를 열고 폴더 업데이트 하 고, 또는 해당 사이트의 기본 페이지를 탐색 SharePoint에서 검색을 수행 하 고 엔터프라이즈 검색 페이지로 이동 하는 것 결과가 반환 됩니다. 확인 합니다.
  
응용 프로그램을 Office 365의 경우 취할 수 있는 가장 기본적인 초기 계획의 일부를 탈출 지점의 또는 네트워크를 유지 하 고 Office 365로 이동 포인트에 네트워크 내의 클라이언트 컴퓨터에서 (밀리초) 시간을 측정 합니다. 일부 조사할 수 있는 유용한 기준 및 레코드 다음과 같습니다.
  
- 클라이언트 컴퓨터 사이 탈출 지점의 프록시 서버에 등 장치를 식별 합니다.
    
  - 상황에 맞는 볼 수 있도록 장치를 알고 있어야 (IP 주소, 장치, 유형의 cetera et) 발생 하는 성능 문제에 대 한 합니다.
    
  - 프록시 서버 일반적인 탈출 포인트 되므로 있는 경우를 사용 하도록 설정 하면 프록시 서버를 확인 하려면 웹 브라우저를 확인할 수 있습니다.
    
  - 검색 및 네트워크를 매핑할 수 있는 타사 도구 있지만 네트워크 팀의 구성원에 게는 장치를 알고 있어야 하는 가장 안전한 방법입니다.
    
- 인터넷 서비스 공급자 (ISP)를 식별 하 고, 연락처 정보를 기록 하 고 및 얼마나 많은 회로, 있는 대역폭을 요청 합니다.
    
- 회사 내부 클라이언트와 탈출 포인트 사이의 장치에 대 한 리소스를 식별 하거나 네트워킹 문제에 대해를 논의할 긴급 연락처를 식별 합니다.
    
이 도구를 사용 하 여 테스트 하는 간단한 일부 기준선 하면 계산할 수 다음과 같습니다.
  
- 밀리초에서 탈출 지점에 클라이언트 컴퓨터에서 시간
    
- 시간 (밀리초) Office 365로 탈출 지점에서 시간
    
- 탐색할 때 Office 365에 대 한 URL을 확인 하는 서버의 세계에서의 위치
    
- 패킷 도착 (네트워크 지터)의 일관성 오류 시간을 밀리초 단위로 ISP의 DNS 확인의 속도 업로드 및 다운로드 시간을 밀리초 단위로
    
다음이 단계를 수행 하는 방법에 익숙한 모르는 경우이 문서에서 더 자세히 살펴보겠습니다. 
  
## <a name="what-is-a-baseline"></a>초기 계획은 무엇입니까?

가 잘못 된, 이동 하지만 어떻게 잘못 된 것 되었을 수 있습니다에 대 한 컨텍스트를 보유할 수 없는 성능 기록 데이터를 모르는 경우 때와 때 영향을 알 수 있습니다. 초기 계획을 없이 퍼즐을 해결 하는 주요 실마리를 누락 된는 되므로: 퍼즐 상자에서 그림입니다. 성능 문제를 해결 해야는 *비교* 지점입니다. 간단한 성능 기준선에 수행 하기 어려운 것은 아닙니다. 일정에 따라 다음을 수행 작업 작업 팀을 수행 될 수 있습니다. 등에 대 한 연결을 다음과 같은 가정해 보겠습니다. 
  
![기본 네트워크 그래픽 클라이언트, 프록시 및 Office 365 클라우드를 표시 합니다.](media/c6ca7140-09f9-4c2d-a775-dbf2820eaa0c.PNG)
  
즉, 네트워크 팀과 함께 검사 하 고 프록시 서버를 통해 인터넷에 대 한 회사를 유지 하 고 클라이언트 컴퓨터는 클라우드로 보내는 모든 요청을 처리 하는 해당 프록시 발견 했습니다. 이 경우 중간에 다른 모든 장치를 나열 하는 대 한 연결의 단순화 된 버전을 그릴 해야 합니다. 이제 Office 365 클라우드 및 (여기서 두면 네트워크는 인터넷에 대 한) 탈출 지점의 클라이언트 간의 성능 테스트에 사용할 수 있는 도구를 삽입 합니다.
  
![클라이언트, 프록시 및 클라우드, 및 추천 PSPing, TraceTCP, 도구를 사용 하 여 기본 네트워크 및 네트워크 추적을 실행 합니다.](media/627bfb77-abf7-4ef1-bbe8-7f8cbe48e1d2.png)
  
옵션은 전문 성능 데이터를 확인 하기 위해 필요한 시간으로 인해 **간단** 하 고 **고급** 으로 나열 됩니다. 네트워크 추적 PsPing 및 TraceTCP와 같은 명령줄 도구를 실행에 비해 시간이 너무 오래 걸립니다. 이러한 두 명령줄 도구는 Office 365에서 차단 되는 ICMP 패킷을 사용 하지 않아 때문에 선택 된 것 및 (있는 경우 access) 클라이언트 컴퓨터 또는 프록시 서버를 유지 하도록 걸리는 하는 시간 (밀리초) 제공 하므로 Office 365에 도착 하 고 있습니다. 시간 값을 가진 다른 한 컴퓨터에서 각 개별 홉 결국 되며, 그 기준선에 대 한 유용한! 중요 한 점은 이러한 명령줄 도구를 사용 하는 명령에 포트 번호를 추가할 수 있습니다, 처럼 Secure Sockets Layer 및 전송 계층 보안 (SSL 및 TLS)에서 사용 되는 포트는 포트 443 통해 통신 하는 Office 365이는 유용 합니다. 그러나 다른 타사 도구 상황에 맞는 더 나은 솔루션 수 있습니다. Microsoft 하지 이러한 도구 중 일부를 지원, 되므로 경우 어떤 이유로 PsPing 및 TraceTCP (영문)를 가져올 수 없습니다 이동할 Netmon 같은 도구를 사용 하 여 네트워크 추적을 합니다. 
  
업무 시간을 많이 사용 하는 동안 다시 하기 전에 초기 계획을 취할 수 있는 다음 시간 후에 다시 합니다. 즉,이 처럼 끝에 좀더 표시 하는 폴더 구조를 할 수 있습니다.
  
![성능 데이터를 폴더로 구성하는 방법을 제시하는 그래픽](media/13e01ffa-f0f2-4d10-b89d-d5980ec89fae.png)
  
또한 파일 명명 규칙을 선택 해야 있습니다. 다음은 몇가지 예입니다.
  
- Feb_09_2015_9amPST_PerfBaseline_Netmon_ClientToEgress_Normal
    
- Jan_10_2015_3pmCST_PerfBaseline_PsPing_ClientToO365_bypassProxy_SLOW
    
- Feb_08_2015_2pmEST_PerfBaseline_BADPerf
    
- Feb_08_2015_8 30amEST_PerfBaseline_GoodPerf
    
이이 작업을 수행 하는 다른 방법 많이 있지만 형식을 사용 하는 ** \<dateTime\>\<테스트에 일어나는\> ** 단체를 시작 합니다. 이 대 한 정확한 중인 데 도움이 됩니다을 많이 나중에 문제를 해결 하 려 할 때. 나중에 말할 수 것 "을 맞 두 추적 년 2 월 8에서 사이 있는 우수한 성능 결과 따르면 하나는 비교할 수 있으므로, 잘못 된 결과 따르면" 합니다. 문제를 해결 하는 것에 대 한 매우 유용합니다. 
  
대화 기록 기준선을 유지 하는 구성 방법이 해야 합니다. 이 예제에서는 간단한 메서드 세 명령줄 출력을 생성 하 고 결과 스크린샷에서,으로 수집 된 있지만 네트워크 캡처 파일 대신 할 수 있습니다. 적합 한 메서드를 사용 합니다. 대화 기록 기준선을 저장 하 고 온라인 서비스의 동작 변경 된 내용을 알게 지점에서 참조 합니다. 
  
## <a name="why-collect-performance-data-during-a-pilot"></a>파일럿 하는 동안 성능 데이터를 수집 이유?

Office 365 서비스의 시험 사용 중 보다 초기 계획을 만들기 시작할 더 나은 시간은 없습니다. 사무실에서 다양 한 사용자가 이미, 수백 수천 또는 해당 될 수 있습니다 5, 있지만 적은 수의 사용자와도 성능의 변동을 측정 하는 테스트를 수행할 수 있습니다. 대기업의 경우 Office 365 파일럿 수행 하는 여러 백 사용자의 대표적인 샘플을 예측할 수 있습니다 바깥쪽으로 다양 한 여러 발생 하기 전에 문제가 발생할 수 있는 알 수 있도록 합니다.
  
여기서 온 보 딩 모든 사용자가 동시에 서비스를 이동 하 고 없는 파일럿은 의미를, 소규모 회사의 경우 잘못 수행 작업 문제를 해결 해야할 수 있는 모든 사용자에 게 표시 하는 데이터를 볼 수 있도록 성능 측정값을 유지 합니다. 예는 갑자기 발견 되 면 될 발생할 수 있는 매우 신속 하 게 사용 하는 중간 규모 그래픽 업로드에 소요 된 시간 내에 건물 주위 탐색할 수 있습니다.
  
## <a name="how-to-collect-baselines"></a>초기 계획을 수집 하는 방법

모든 문제해결 계획에 대 한 여기에 최소한 이러한 작업을 파악 해야 합니다.
  
- 클라이언트 컴퓨터 (컴퓨터 또는 장치, IP 주소 및 문제를 발생 시킨 작업의 유형)를 사용 하는
    
- 클라이언트 컴퓨터의 위치는 세계 (하는지 여부 등이 사용자는 회사 인트라넷 또는 원격으로 작업 하는 네트워크에 대 한 VPN에)
    
- 네트워크에서 탈출 지점의 클라이언트 컴퓨터를 사용 하 여 (ISP 또는 인터넷에 대 한 트래픽을 떠나는 비즈니스는 지점)
    
 네트워크 관리자 로부터 네트워크의 레이아웃을 찾을 수 있습니다. 소규모 네트워크에 속해에서 인터넷에 연결 하면 장치에 대 한 정보를 수행 하 고 레이아웃에 대 한 질문이 있는 경우에 ISP를 호출 합니다. 참조용으로 최종 레이아웃의 그래픽을 만듭니다. 
  
이 섹션은 간단한 명령줄 도구 및 방법, 나누어 하 고 더 많은 고급 도구 옵션입니다. 먼저 간단한 방법 설명 하겠습니다. 하지만 설치 되었으면 성능 문제를 지금 바로, 고급 방법으로 이동 하 고 샘플 성능 문제를 해결 작업 계획을 사용해 해야 합니다.
  
### <a name="simple-methods"></a>간단한 메서드

간단한 이러한 방법 중 목적은 걸릴 이해 하 고 시간에 따른 간단한 성능 기준선을 저장 하 Office 365 성능에 대 한 정보는 제대로 하는 방법을 알아봅니다. 지금까지 하기 전에 살펴본 대로 간단 하 고에 대 한 매우 간단한 다이어그램 다음과 같습니다.
  
![클라이언트, 프록시 및 클라우드, 및 추천 PSPing, TraceTCP, 도구를 사용 하 여 기본 네트워크 및 네트워크 추적을 실행 합니다.](media/627bfb77-abf7-4ef1-bbe8-7f8cbe48e1d2.png)
  
> [!NOTE]
> TraceTCP 표시, 시간을 밀리초 단위로 요청 걸리는 프로세스 및 얼마나 많은 네트워크 홉 또는 연결에는 다음에 한 컴퓨터에서 요청을 대상에 도달 하는 시간이 위한 유용한 도구 이기 때문에이 화면에 포함 됩니다. TraceTCP 홉 지원에는 Microsoft Office 365 문제 해결사에 유용할 수 있는 하는 동안 사용 되는 서버의 이름을 제공할 수도 있습니다. > TraceTCP 명령을와 같은 매우 간단한 수: > `tracetcp.exe outlook.office365.com:443`> 명령에 포트 번호를 포함 하도록 기억! > [TraceTCP](https://simulatedsimian.github.io/tracetcp.mdl) 는 무료 다운로드 하지만 Wincap에 의존 합니다. Wincap는 또한 사용 되 고 Netmon 하 여 설치 하는 도구입니다. 또한 네트워크 모니터를 사용 하 여 고급 방법 섹션에서 합니다. 
  
 여러 사무실을 설치한 경우에 해당 위치의 각 클라이언트에서 데이터 집합을 변경 하지 않으려면 필요 합니다. 이 테스트는이 경우에 Office 365 및 Office 365의 요청에 대 한 응답을 요청을 보내는 클라이언트 사이의 시간을 설명 하는 숫자 값은 대기 시간을 측정 합니다. 테스트는 클라이언트 컴퓨터에서 도메인 내 발생 하 고를 Office 365에 인터넷을 통해 탈출 지점의 통해 네트워크 내부에서 대 한 왕복을 측정 하 여 백업를 찾습니다. 
  
탈출 지점의이 경우 프록시 서버를 처리 하는 몇가지 방법이 있습니다. 2 및 다음 2-3, 1에서 추적 수 있으며 네트워크의에 지에 최종 합계를 구하려면 시간 (밀리초)에는 번호를 추가 합니다. 또는 Office 365 주소에 대 한 프록시를 우회에 대 한 연결을 구성할 수 있습니다. 방화벽, 역방향 프록시 또는 둘의 일부 조합을 더 큰 네트워크에서 많은 양의 Url에 대 한 전달에 대 한 트래픽을 선택 하면 프록시 서버에서 예외를 확인 해야할 수 있습니다. Office 365에서 사용 하는 끝점의 목록, [Office 365 Url 및 IP 주소 범위를](https://support.office.com/article/8548a211-3fe7-47cb-abb1-355ea5aa88a2)참조 하십시오. 인증 된 프록시를 사용 하는 경우 다음에 대 한 예외를 테스트 하 여 시작 합니다.
  
- 포트 80 및 443
    
- TCP 및 HTTPs
    
- 이러한 Url 중 하나로 아웃 바운드 된 연결:
    
- \*. microsoftonline.com
    
- \*.microsoftonline p.com
    
- \*. sharepoint.com
    
- \*. outlook.com
    
- \*. lync.com
    
- osub.microsoft.com
    
모든 사용자 모든 프록시 간섭 또는 인증 없이 이러한 주소를 허용 해야 합니다. 더 작은 네트워크에서 웹 브라우저에서 목록 바이패스이 프록시를 추가 해야 합니다. 
  
프록시 바이패스 목록에 이러한를 Internet Explorer에서 추가 하려면 **도구** 이동 \> **인터넷 옵션** \> **연결** \> **LAN 설정** 을 \> **고급**합니다. 고급 탭은 또한 프록시 서버와 프록시 서버 포트를 찾을 수 있습니다. **사용자 LAN에 프록시 서버 사용**, **고급** 단추에 액세스 하려면 확인란을 클릭 해야 합니다. **로컬 주소에 프록시 서버 사용 안함** 선택 되었는지 확인 합니다. **고급**을 클릭 한 후에 예외를 입력할 수 있는 텍스트 상자를 표시 됩니다. 위에 나열 된 세미콜론으로 구분와 같이 와일드 카드 Url을 구분 합니다.
  
\*. microsoftonline.com; \*. sharepoint.com
  
프록시를 무시 되 면는 Office 365 URL에서 직접 ping 또는 PsPing를 사용할 수 있게 해야 합니다. 다음 단계는 ping **outlook.office365.com**를 테스트할 수 있습니다. 또는 PsPing 또는 다른 도구를 사용 하는 경우 사용자에 게 평균 왕복 시간 (밀리초) 참조 하려면 **portal.microsoftonline.com:443** 에 대해 PsPing 명령에 포트 번호를 제공할 수 있도록 합니다. 
  
왕복 시간 또는 RTT은 outlook.office365.com와 같은 서버에 HTTP 요청을 보내고 서버 것 사실을 알고 있는 것을 승인 하는 응답을 다시 가져오려면 걸리는 시간을 측정 하는 숫자 값입니다. 가끔 RTT 약어이 볼 수 있습니다. 이 비교적 짧은 시간 동안 이어야 합니다.
  
[PSPing](https://technet.microsoft.com/en-us/sysinternals/jj729731.aspx) 또는 ICMP 패킷을이 테스트를 수행 하기 위해 Office 365에 의해 차단 되는 사용 하지 않는 다른 도구를 사용 해야 합니다. 
  
 **사용 하 여 PsPing를 전반적으로 왕복 시간 (밀리초)에는 Office 365 URL에서 직접 하는 방법**
  
1. 다음이 단계를 완료 하 여 관리자 권한 명령 프롬프트를 실행 합니다.
    
1. **시작**을 클릭합니다.
    
2. **검색 시작** 상자에 cmd를 입력 한 다음 CTRL + SHIFT + ENTER 키를 누릅니다.
    
3. **사용자 계정 컨트롤** 대화 상자가 나타나면 대화 상자에서 표시되는 동작이 원하는 동작인지 확인하고 **계속**을 클릭합니다.
    
2. 도구 (이 경우 PsPing)에서 설치 된 폴더로 이동 하 고 이러한 Office 365 Url을 테스트 합니다.
    
  - psping portal.office.com:443
    
  - psping microsoft my.sharepoint.com:443
    
  - psping outlook.office365.com:443
    
  - psping www.yammer.com:443
    
    ![Microsoft my.sharepoint.com 포트 443 하려고 PSPing 명령입니다.](media/3258f620-4513-4e82-95c9-06b387fc3a82.PNG)
  
443 포트 번호를 포함 해야 합니다. Office 365 암호화 된 채널에서 작동 해야 합니다. 하면 포트 번호가 없는 PsPing, 요청이 실패 합니다. 몇 명에 ping 했을 때을 한 후 평균 시간 (ms)를 찾습니다. 즉, 기록 하려는!
  
![표시 하는 그래픽 클라이언트의 그림이 2.8 밀리초 왕복 시간으로 PSPing 프록시에 있습니다.](media/96901aea-1093-4f1b-b5a3-6078e9035e6c.png)
  
프록시 바이패스 잘 모르는 단계별 작업을 수행 하는 것을 선호 하는 경우 먼저 프록시 서버의 이름을 확인 해야 합니다. Internet Explorer에서 **도구** 이동 \> **인터넷 옵션** \> **연결** \> **LAN 설정** 을 \> **고급**합니다. **고급** 탭은 나열 된 프록시 서버에 나타납니다. 이 작업을 완료 하 여 해당 프록시 서버의 명령 프롬프트에 ping을 사용 합니다. 
  
 **프록시 서버에 ping 및 1 ~ 2 단계에 대 한 밀리초에서 왕복 값을 가져오려면**
  
1. 다음이 단계를 완료 하 여 관리자 권한 명령 프롬프트를 실행 합니다.
    
1. **시작**을 클릭합니다.
    
2. **검색 시작** 상자에 cmd를 입력 한 다음 CTRL + SHIFT + ENTER 키를 누릅니다.
    
3. **사용자 계정 컨트롤** 대화 상자가 나타나면 대화 상자에서 표시되는 동작이 원하는 동작인지 확인하고 **계속**을 클릭합니다.
    
2. 형식은 ping \<프록시 서버의 이름을 브라우저 사용 하 여 또는 프록시 서버의 IP 주소\> 한 다음 ENTER 키를 누릅니다. PsPing, 또는 일부 다른 도구를 설치 하는 경우에 대신 해당 도구를 사용 하도록 선택할 수 있습니다. 
    
    명령이 이러한 예 중 하나라도 다음과 같을 수 있습니다. 
    
  - ping ourproxy.ourdomain.industry.business.com
    
  - ping 155.55.121.55
    
  - ping ourproxy
    
  - psping ourproxy.ourdomain.industry.business.com:80
    
  - psping 155.55.121.55:80
    
  - psping ourproxy:80
    
3. 추적 중지 테스트 패킷을 전송 되는 평균 시간 (밀리초)를 나열 하 고 후 자신이 값 작은 요약을 얻을 수 있습니다. 스크린샷 프롬프트를 수행 하 고 명명 규칙을 사용 하 여 저장 합니다. 이 시점에서 값을 가진 다이어그램에 맞게 도움이 될 수 있습니다.
    
초기 아침에서 추적을 수행 했을 때 엔터프라이즈 무선 전화 통신 하 고 클라이언트는 프록시 (또는 인터넷에 관계 없이 탈출 서버를 종료할)을 신속 하 게 얻을 수 있습니다. 이 경우 번호는 다음과 같을 수 있습니다.
  
![표시 하는 그래픽 왕복 시간 클라이언트에서 프록시 2.8 시간 (밀리초)입니다.](media/1bd03544-23fc-47d4-bbae-c1feb466a5d8.PNG)
  
클라이언트 컴퓨터가 프록시 (또는 탈출) 서버에 액세스할 수 있는 선택 된 몇몇 중 하나에 하는 경우 명령 프롬프트에서에서 Office 365 URL로 PsPing를 실행 하는 테스트의 다음 레그 해당 컴퓨터에 원격으로 연결 하 여 실행할 수 있습니다. 해당 컴퓨터에 대 한 액세스를 설치 하지 않은 경우 다음 레그에 대 한 지원에 대 한 네트워크 리소스에 문의할 수 있습니다 하 고 정확 하 게 하면 해당 방식으로 번호를 매깁니다. 가능 하지 않은 경우 Office 365 URL에 대해 PsPing 문제의 걸리고 프록시 서버에 대해 PsPing 또는 Ping 시간을 비교 합니다. 
  
등 51.84 시간 (밀리초) 클라이언트에서 Office 365 URL에 있고 2.8 시간 (밀리초) 클라이언트에서 프록시 (또는 탈출 지점)에 있는 다음 있으면 Office 365에는 탈출에서 49.04 밀리초입니다. 마찬가지로, 일과 62.01 시간 (밀리초) 클라이언트에서 Office 365 URL의 높이 동안 12.25 시간 (밀리초) 클라이언트에서 프록시에 PsPing을 설치한 경우 Office 365 URL로 프록시 탈출에 대 한 평균 값은 49.76 밀리초입니다.
  
![추가 보여주는 그래픽 ping 밀리초에서 클라이언트에서 Office 365에 클라이언트 옆에 있는 프록시에는 값을 뺍니다 수 있도록 합니다.](media/cd764e77-5154-44ba-a5cd-443a628eb2d9.PNG)
  
이 문제를 해결 하는 것 이라는 측면에서 이러한 기준선 유지에서 방금 흥미로운를 찾을 수 있습니다. 예, 일반적으로 있는 것에 대 한 확인 하는 경우 프록시 또는 탈출에서 대기 시간을 밀리초 단위로 40 ~ 59 Office 365 URL을 가리키도록 되어 프록시 또는 탈출 지점 대기 시간이 3 ~ 7 시간 (밀리초)에 대 한 클라이언트 (하면 트래픽 양 네트워크에 따라 seein는 해당 시간 동안 g) 다음 분명 프록시 또는 탈출 기준선에 마지막 세 클라이언트 45 시간 (밀리초)을 대기 시간을 표시 하는 경우 문제가 있는 것을 알 수 있습니다.
  
### <a name="advanced-methods"></a>고급 메서드

Office 365로 인터넷 요청으로 소식 하려는 경우 네트워크 추적을 숙지 해야 합니다. 으로 해당 도구 수 캡처 및 네트워크 트래픽을 필터링 수행 됩니다 다른 하 든 HTTPWatch, Netmon, 메시지 분석기, Wireshark, Fiddler, 개발자 대시보드 도구 이러한 추적에 대 한 선호 하는 도구는 중요 하지 않습니다. 이 섹션에서 이러한 도구를 사용 하는 문제를 완벽 하 게 파악할 중 하나 이상를 실행 하는 것이 좋습니다 인지 표시 됩니다. 테스트 하는 경우 이러한 도구 중 일부 역할을 할 수도 자신의 오른쪽에 있는 프록시 합니다. [Netmon 3.4](https://www.microsoft.com/en-us/download/details.aspx?id=4865), [HTTPWatch](https://www.httpwatch.com/download/)또는 [WireShark](https://www.wireshark.org/) [성능 문제해결 Office 365에 대 한 계획](performance-troubleshooting-plan.md), companion 문서의 사용 되는 도구를 포함 합니다.
  
이 메서드의 간단한 부분 성능 기준선을 하는 것이 되며 대부분의 단계와 동일 하 게 성능 문제를 해결 하는 경우. 성능에 대 한 초기 계획을 작성 하는 고급 방법 필요를 수행 하 고 네트워크 추적을 저장 합니다. 대부분의이 문서의 예제를 사용 하 여 SharePoint Online, 하지만 테스트 하 고 기록에 가입 하는 Office 365 서비스 간에 공통 작업 목록을 개발 해야 합니다. 초기 계획 예제는 다음과 같습니다.
  
- SPO-에 대 한 초기 계획 목록 * * 1 단계: * * 찾아보기 홈페이지의 SPO 웹사이트 및 네트워크 추적을 수행 합니다. 추적을 저장 합니다. 
    
- SPO-에 대 한 초기 계획 목록 **2 단계:** 엔터프라이즈 검색을 실행 한 네트워크 추적을 통해 (예: 회사 이름) 용어에 대 한 검색 합니다. 추적을 저장 합니다. 
    
- SPO-에 대 한 초기 계획 목록 **3 단계:** SharePoint 온라인 문서 라이브러리 및 네트워크 추적을 수행 하는 대용량 파일 업로드 합니다. 추적을 저장 합니다. 
    
- SPO-에 대 한 초기 계획 목록 **4 단계:** 찾아보기 홈페이지의 OneDrive 웹사이트 및 네트워크 추적을 수행 합니다. 추적을 저장 합니다. 
    
이 목록은 SharePoint Online에 대해 사용자를 사용 하는 가장 중요 한 일반적인 작업을 포함 해야 합니다. 에서 볼 수 있듯이, 비즈니스용 OneDrive를 추적 하는 마지막 단계, 빌드-거의 하도록 사용자 지정 비즈니스 홈 페이지에 대 한 (하는 회사에서 사용자 지정 종종 된) SharePoint Online 홈페이지의 부하와 OneDrive 간의 비교 합니다. 느린 로드 SharePoint Online 사이트를 사용할 때에이 매우 기본적인 테스트 합니다. 테스트에이 차이 대 한 레코드를 만들 수 있습니다.
  
성능 문제를 가운데에 경우 대부분의 단계와 같습니다 초기 라인 상태로 전환할 때 합니다. 네트워크 추적을 실행 될는 게 처리 하는 *방법* 의 중요 한 추적을 실행 하려면 다음 있으므로 중요 합니다. 
  
*지금 바로* , 성능 문제를 해결할 성능 문제가 발생 하는 시간에 대체를 추적 하 게 될 필요 합니다. 로그를 수집 하기 위해 사용할 수 있는 적절 한 도구 해야 하 고 작업 계획, 즉, 목록이 수 있는 최상의 정보를 수집 하기 위해 수행할 작업을 문제를 해결 해야 합니다. 가장 먼저 할 일은 파일 타이밍을 반영 하는 폴더에 저장 될 수 있도록 테스트의 시간과 날짜를 기록 합니다. 다음으로 범위를 좁힐 자체 문제 단계입니다. 다음은 테스트에 사용할는 정확한 단계입니다. 기본 사항 잊지 마십시오: 하나만 Office 365 서비스에서 문제가 발생 하는 레코드를 Outlook에만 문제가 있는 경우 있는지 확인 합니다. 이 문제의 범위를 좁힐 수 있는 해결 하는 것에 초점을 하는데 도움이 됩니다. 
  
## <a name="see-also"></a>참고 항목

[Office 365 끝점 관리](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a)
