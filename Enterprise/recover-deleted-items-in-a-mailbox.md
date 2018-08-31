---
title: 사용자 사서함에서 지운 편지함 복구 - 관리자 도움말
ms.author: markjjo
author: markjjo
manager: laurawi
ms.date: 6/29/2018
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
- MOE150
- MED150
- MBS150
- BCS160
ms.assetid: eb15194b-63ec-41b0-8d90-1823d3f558e4
description: '이 문서는 관리자입니다. 않은 사용자 항목을 영구히 삭제 자신의 Outlook 사서함에서? 사용자는 다시가 하려는 있지만 복구할 수 없습니다. 수은 하지 않은 제거 된 경우 영구적으로 사용자의 사서함에서 제거 된 항목을 복구 합니다. '
ms.openlocfilehash: abfc0a1a35d8e694197e12d05a2206dd4e3eb37a
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/27/2018
ms.locfileid: "22541972"
---
# <a name="recover-deleted-items-in-a-user-mailbox---admin-help"></a>사용자 사서함에서 지운 편지함 복구 - 관리자 도움말

**관리자를 위한이 문서는. 자신의 사서함에 있는 삭제 된 항목을 복구 하려고 합니까?** 다음 중 하나를 수행 합니다.
- [Windows용 Outlook에서 삭제된 항목 복구](https://support.office.com/article/49e81f3c-c8f4-4426-a0b9-c0fd751d48ce)
- [Outlook Web App에서 지운 편지함 또는 전자 메일 복구](https://support.office.com/article/c3d8fc15-eeef-4f1c-81df-e27964b7edd4)
- [웹에 있는 Outlook에서 삭제 된 전자 메일 메시지를 복원 합니다.](https://support.office.com/article/a8ca78ac-4721-4066-95dd-571842e9fb11)
- [Outlook.com](https://go.microsoft.com/fwlink/p/?LinkID=623435)
   
않은 사용자 항목을 영구히 삭제 자신의 Outlook 사서함에서? 사용자는 다시가 하려는 있지만 복구할 수 없습니다. 수은 하지 않은 제거 된 경우 영구적으로 사용자의 사서함에서 제거 된 항목을 복구 합니다. Exchange Online에서 원본 위치 eDiscovery 도구를 사용 하 여 삭제 된 전자 메일 및 기타 항목을 검색 하 여이 작업을 수행-연락처, 일정 약속 및 작업 같은 및-사용자의 사서함에 있습니다. 삭제 된 항목을 찾을 수 있으면 PST 파일 (Outlook 데이터 파일 라고도 함), 사용자가 사서함에 다시 항목을 복원 하려면 사용 하 여 수를 내보낼 수 있습니다.
  
사용자의 사서함에서 삭제 된 항목을 복구 하는 중에 대 한 단계는 다음과 같습니다. 이 소요시간? 처음으로 복구 하려는 경우 얼마나 많은 항목에 따라 단계를 모두 완료 하는 데 20 또는 30 분 걸릴 수 있습니다.
  
> [!NOTE]
> 가 **Exchange 관리자** 또는 Office 365에서 **전역 관리자** 또는 조직 관리 역할 그룹의 구성원 Exchange Online에서 수이 문서의 단계를 수행 하려면 해야 합니다. 자세한 내용은 [Office 365에 대 한 관리자 역할](https://support.office.com/article/da585eea-f576-4f55-a1e0-87090b6aaa9d)을 참조 하십시오. 
  
## <a name="step-1-assign-yourself-ediscovery-permissions"></a>1 단계: eDiscovery 사용 권한을 직접 할당
<a name="step1"> </a>

먼저 할당 하는 것 사용자가 직접 필요한 사용 권한을 Exchange 온라인 사용자의 사서함을 검색 하는 원본 위치 eDiscovery 도구를 사용할 수 있도록 합니다. 이 작업을 한번 수행 해야 합니다. 다른 사서함을 나중에 검색 해야하는 경우에이 단계를 건너뛸 수 있습니다.
  
1. [비즈니스를 위한 Office 365에 로그인 할 위치](https://support.office.com/article/e9eb7d51-5430-4929-91ab-6157c5a050b4) 선택 하면 작업이 나 교육용 계정과 합니다. 
    
2. 응용 프로그램 시작 관리자 아이콘을 선택 ![Office 365에 있는 응용 프로그램 시작 관리자 아이콘](media/7502f4ec-3c9a-435d-a7b4-b9cda85189a7.png) 왼쪽 위에서에서 **관리**를 클릭 하 고 있습니다.
    
3. Office 365 관리 센터의 왼쪽 탐색 영역에서 **관리 센터**를 확장 하 고 **Exchange**를 클릭 합니다.
    
    ![관리 센터 목록](media/7d308eb7-ba63-4156-a845-3770facc5de4.PNG)
  
4. Exchange 관리 센터에서 **사용 권한**을 클릭 한 다음 **관리 역할**을 클릭 합니다.
    
5. 목록 보기에서 **검색 관리**선택 하 고 **편집**을 클릭 한 다음![편집 아이콘](media/ebd260e4-3556-4fb0-b0bb-cc489773042c.gif)합니다.
    
    ![EAC에서 검색 관리 역할 그룹에 추가 하는 사용자가 직접](media/e5c98e93-d6a0-40c5-a143-bac956eedaa7.png)
  
6. **역할 그룹** **구성원**아래에서 **추가**클릭![추가 아이콘](media/8ee52980-254b-440b-99a2-18d068de62d3.gif)합니다.
    
7. **구성원 선택**는 이름 목록에서 자신을 선택 하 고 **추가**클릭 한 다음 **확인**을 클릭 합니다.
    
    > [!NOTE]
    > 조직 관리 또는 TenantAdmins 등,의 구성원 이어야 하는 그룹을 추가할 수도 있습니다. 그룹에 추가 하면 다른 구성원 그룹의 원본 위치 eDiscovery 도구를 실행 하려면 필요한 권한은 할당 됩니다. 
  
8. **역할 그룹** **저장** 을 클릭 합니다.
    
9. Office 365에서 로그 아웃 합니다.
    
    새 사용 권한을 적용 되도록 다음 단계를 시작 하기 전에 로그 아웃 해야 합니다.
    
> [!CAUTION]
> 검색 관리 역할 그룹의 구성원에는 중요 한 메시지 콘텐츠에 액세스할 수 있습니다. 조직에서 모든 사서함을 검색, 검색 결과 (및 기타 사서함 항목)를 미리 보거나, 결과 검색 사서함으로 복사 및 PST 파일로 검색 결과 내보내기 (영문)이 포함 됩니다. 
  
[Return to top](recover-deleted-items-in-a-mailbox.md#__top)
  
## <a name="step-2-search-the-users-mailbox-for-deleted-items"></a>삭제 된 항목에 대 한 사용자의 사서함을 검색 하는 2 단계:
<a name="step2"> </a>

원본 위치 eDiscovery 검색을 실행 하면 검색 하는 사서함의 복구 가능한 항목 폴더의 검색에 자동으로 포함 됩니다. 복구 가능한 항목 폴더에서 영구적으로 삭제 된 항목 저장 된 위치 (영구적으로 제거)을 제거 하려는 자신이 때까지 사서함에서은입니다. 따라서 항목을 제거한 하지 않은 경우에 원본 위치 eDiscovery 도구를 사용 하 여 찾을 수 있습니다.
  
1. [비즈니스를 위한 Office 365에 로그인 할 위치](https://support.office.com/article/e9eb7d51-5430-4929-91ab-6157c5a050b4) 선택 하면 작업이 나 교육용 계정과 합니다. 
    
2. 응용 프로그램 시작 관리자 아이콘을 선택 ![Office 365에 있는 응용 프로그램 시작 관리자 아이콘](media/7502f4ec-3c9a-435d-a7b4-b9cda85189a7.png) 왼쪽 위에서에서 **관리**를 클릭 하 고 있습니다.
    
3. Office 365 관리 센터의 왼쪽 탐색 영역에서 **관리**확장 한 다음 **Exchange**를 클릭 합니다.
    
4. Exchange 관리 센터에서 **준수 관리**, 클릭 **원본 위치 eDiscovery &amp; 유지**, **새로 만들기**를 클릭 하 고![추가 아이콘](media/8ee52980-254b-440b-99a2-18d068de62d3.gif)합니다.
    
    ![EAC의 규정 준수 관리 페이지에서 원본 위치 eDiscovery 클릭 및 유지](media/9d9ff0f5-b9be-45b8-8b5e-6037a856b0a8.png)
  
5. **이름 및 설명** 페이지에서 검색 (예: 전자 메일에 대 한 복구 중인 사용자의 이름), 선택적 설명 및 클릭에 대 한 이름을 입력 **다음**합니다.
    
6. **사서함** 페이지에서 **지정 사서함 검색을**클릭 하 고 **추가**클릭 한 다음![추가 아이콘](media/8ee52980-254b-440b-99a2-18d068de62d3.gif)합니다.
    
    ![특정 사서함을 검색 하려면 검색 하도록 지정 사서함을 클릭 합니다.](media/83879a40-5e5c-49a8-be3b-c0023d197588.png)
  
7. 찾기 및에 대 한 삭제 된 전자 메일을 복구 하는 사용자의 이름을 선택, **추가**클릭 한 다음 **확인**을 클릭 합니다.
    
8. **다음**을 클릭합니다.
    
    **검색 쿼리** 페이지가 표시 됩니다. 사용자의 사서함에서 누락 된 항목을 찾을 수 있는 검색 조건을 정의 하는 위치입니다. 
    
9. **검색 쿼리** 페이지에서 다음 필드를 작성합니다. 
    
  - **모든 콘텐츠를 포함 합니다.** 검색 결과에서 사용자의 사서함에 모든 콘텐츠를 포함 하려면이 옵션을 선택 합니다. 이 옵션을 선택 하는 경우에 추가 검색 조건을 지정할 수 없습니다. 
    
  - **필터 조건에 따라** 시작 하는 키워드를 포함 한 검색 조건을 지정 하 고 끝 날짜, 보낸사람 및 받는 사람 주소와 메시지 유형 하려면이 옵션을 선택 합니다. 
    
    ![키워드, 날짜 범위, 받는 사람 및 메시지 유형 같은 기준에 따라 검색 작성](media/ee47b833-9122-46a0-85e6-fcbe25be0dd5.png)
  
|**필드**|**하려면이 옵션을 사용 하 여...**|
|:-----|:-----|
|![분홍색 원에서 번호 1](media/a4da261d-2516-48c5-b58a-9c452b9086b8.png)           <br/> |키워드, 날짜 범위, 받는 사람 및 메시지 유형을 지정 합니다.  <br/> |
|![분홍색 원에 두 번호입니다.](media/de3c1ab4-4f01-4026-b1ba-3265bdb32a89.png)           <br/> |키워드 또는 구를, 메시지에 대 한 검색 하 고 **AND** 또는 **OR**같은 논리 연산자를 사용 합니다.  <br/> |
|![분홍색 원에서 3 번호입니다.](media/60fa378c-6ac1-4cbd-a782-2fa7ca619dc6.png)           <br/> |날짜 범위 내에서 보내거나 받은 메시지를 검색 합니다.  <br/> |
|![분홍색 원에 4 번호입니다.](media/1a0ff2ce-0942-405a-94e3-9bfeb1e5059e.png)           <br/> |받거나 특정인에 게 보낸 메시지를 검색 합니다.  <br/> |
|![번호 매기기 5 분홍색 원입니다.](media/878cc815-0165-49ba-a1ee-9236e5980403.png)           <br/> |모든 메시지 유형이 검색 하거나 특정 위치를 선택 합니다.  <br/> |
   
    > [!TIP]
    >  Here's a few tips about how to build a search query to find missing items. Try to get as much information from the user to help you create a search query so you can find what you're looking for. >  If you not sure how to find a missing message, consider using the **Include all content** option. The search results will include all items in the user's Recoverable Items folder, including the hidden folder (called the Purges folder) that contain items that have been purged by the user. Then you can go to Step 3, copy the results to a discovery mailbox, and look at the message in the hidden folder. >  If you know approximately when the missing message was originally sent or received by the user, use the **Specify start date** and **Specify end date** options to provide a date range. This will return all messages sent or received by the user within that date range. Specifying a date range is a really good way to narrow the search results. >  If you know who sent the missing email, use the **From** box to specify this sender. >  If you want to narrow the search results to different types of mailbox items, click **Select message types**, click **Select the message types to search**, and then choose a specific message type to search for. For example, you can search only for calendar items or contacts. Here's a screenshot of the different message types you can search for; the default is to search for all message types. 
  
    Click **Next** when you've completed the **Search query** page. 
    
10. **원본 위치 유지 설정** 페이지에서 검색을 시작 하려면 **완료** 를 클릭 합니다. 삭제 된 전자 메일을 복구 하는 사용자의 사서함을 보류 하 이유가 있습니다. 
    
    검색을 시작 하면 Exchange의 예상 전체 크기 및 지정한 조건에 따라 검색에 의해 반환 되는 항목 수가 표시 됩니다.
    
11. 방금 만든 검색을 선택 하 고 **새로 고칠**을 클릭![새로고침](media/165fb3ad-38a8-4dd9-9e76-296aefd96334.png) 세부 정보 창에 표시 되는 정보를 업데이트 합니다. **예측 성공** 의 상태를 검색 완료 되었음을 나타냅니다. Exchange에는 9 단계에서 지정한 검색 조건을 기준으로 검색 하 여 항목 (및 해당 크기)의 총 수를 예상 표시 됩니다. 
    
12. 세부 정보 창에서 발견 된 항목을 볼 수 있는 **검색 결과 미리 보기를** 클릭 합니다. 항목을 찾는 식별 도움이 될 수 있습니다이 있습니다. 복구 하려는 항목을 찾을 수 있으면 검색 결과 PST 파일로 내보낼 4 단계로 이동 합니다. 
    
    ![검색 결과를 복구 하려는 항목을 보려면 미리 보기를 클릭 합니다.](media/a2cea921-dafa-45d6-97d4-ae45a226b8d3.png)
  
13. 원하는 내용을 찾을 수 없는 경우 수정할 수 있습니다 검색 조건을 검색을 선택 하 여 **편집**을 클릭 하면![편집 아이콘](media/ebd260e4-3556-4fb0-b0bb-cc489773042c.gif), 다음 **검색 쿼리**를 클릭 하 고 있습니다. 검색 조건을 변경 하 고 검색을 다시 실행 합니다.
    
[Return to top](recover-deleted-items-in-a-mailbox.md#__top)
  
## <a name="optional-step-3-copy-the-search-results-to-a-discovery-mailbox"></a>(선택 사항) 3 단계: 검색 결과 검색 사서함으로 복사
<a name="step3"> </a>

검색 결과 미리 보고 한 항목을 찾을 수 없는 경우 또는 사용자의 복구 가능한 항목 폴더에는 되는 항목을 참조 하려면 다음 검색 결과 (검색 사서함 라고 함) 특별 한 사서함에 복사한 후 t 웹에서 Outlook에서 해당 사서함을 엽니다. o는 실제 항목을 봅니다. 검색 결과 복사 하는 가장 좋은 이유 이므로 사용자의 복구 가능한 항목 폴더에서 항목을 볼 수 있습니다. 복구 하려는 항목 제거 하위 폴더에 있는 가능성이 높습니다. 
  
1. Exchange 관리 센터에서 **준수 관리** 로 이동 \> **원본 위치 eDiscovery &amp; 유지**합니다.
    
2. 검색의 목록에서 2 단계에서에서 만든 검색을 선택 합니다.
    
3. **검색**을 클릭![검색](media/c94e8591-7044-4650-a0d1-c57c0633ab4f.png), 한 다음 드롭다운 목록에서 **검색 결과 복사를** 클릭 합니다. 
    
    ![검색을 클릭 한 다음 검색 결과 복사를 클릭 합니다.](media/7888df82-94b4-4e44-8a53-f66854dc7c86.png)
  
4. **복사본 검색 결과** 페이지에서 **찾아보기**를 클릭 합니다.
    
    ![삭제 된 항목을 복구 하는 경우 옵션의 선택을 취소 하는 확인란을 그대로 둡니다.](media/37f27999-a5b2-4fed-87e2-bad6dc23cdae.png)
  
5. **표시 이름**아래에서 **사서함 검색**클릭 한 다음 **확인**을 클릭 합니다.
    
    ![기본 검색 사서함을 검색 결과 복사](media/36e8ef47-0035-4982-9ed6-426719c5f9ec.png)
  
    > [!NOTE]
    > 사서함 검색은 Office 365 조직에 자동으로 생성 된 기본 검색 사서함입니다. 
  
6. **복사본 검색 결과** 페이지에 다시 사서함 검색에 검색 결과 복사 하 여 프로세스를 시작 **복사** 클릭 합니다. 
    
    ![사서함 검색에 검색 결과 복사 하려면 복사를 클릭 합니다.](media/71307a9d-f7a1-4e01-ae37-1d49040cc3fd.png)
  
7. **새로고침**을 클릭![새로고침](media/165fb3ad-38a8-4dd9-9e76-296aefd96334.png) 세부 정보 창에 표시 되는 복사 상태에 대 한 정보를 업데이트 합니다. 
    
8. 복사가 완료 되 면 검색 결과 보려면 검색 검색 사서함을 열려면 **열기** 를 클릭 합니다. 
    
    ![검색 결과 보려면 검색 검색 사서함으로 이동 하는 열기를 클릭 합니다.](media/6cc81e0f-ceed-4464-9040-79b6f920de35.png)
  
    검색 검색 사서함에 복사 하는 검색 결과 원본 위치 eDiscovery 검색 이름이 같은 폴더에 배치 됩니다. 해당 폴더에 있는 항목을 표시 하는 폴더를 클릭 합니다.
    
    ![사서함 검색;에서 검색 결과 제거 폴더의 항목을 관리 하 여 복구할 수 있습니다.](media/2ef8e5fb-3e63-4f62-938e-307efe9f6998.gif)
  
    검색을 실행 하는 경우에 사용자의 복구 가능한 항목 폴더 검색도 됩니다. 즉, 검색 결과에 포함 된 복구 가능한 항목 폴더에서 항목 검색 조건을 충족 하는 경우. 삭제 폴더의 항목은 사용자 (지운 편지함 폴더에서 항목을 삭제 하 여 또는 선택 하 고 **Shift + Delete**키를 눌러 여를 영구적으로 삭제 하는 항목. 사용자는 Outlook 또는 웹에 있는 Outlook에서 지운 편지함 복구 도구를 사용 하 여 삭제 폴더에서 항목을 복구할 수 있습니다. 제거 폴더의 항목은 지운 편지함 복구 도구를 사용 하 여 사용자를 제거 하는 항목 또는 사서함에 적용 된 정책에 의해 제거 된 자동으로 된 항목입니다. 두 경우 모두에서 관리자만 제거 폴더에서 항목을 복구할 수 있습니다. 
    
    > [!TIP]
    > 사용자는 복구 가능한 항목 도구를 사용 하 여 삭제 된 항목을 찾을 수 없는 하 고 해당 항목은 여전히 복구할 수 (있는지 것 하지 않은 영구적으로 제거 된 사서함에서 의미), 것은 것이 더 폴더에 있는 제거 합니다. 그렇다면 사용자에 대 한 복구 하려는 삭제 된 항목에 대 한 제거 폴더에서 검토 해야 합니다. 
  
[Return to top](recover-deleted-items-in-a-mailbox.md#__top)
  
## <a name="step-4-export-the-search-results-to-a-pst-file"></a>4 단계: 검색 결과 PST 파일로 내보내기
<a name="step4"> </a>

사용자에 대 한 복구 하려는 항목을 찾은 후 다음 단계를 PST 파일로 2 단계에서에서 실행 하는 검색에서 결과 내보내는입니다. 사용자가 사서함에 삭제 된 항목을 복원 하려면 다음 단계에서이 PST 파일을 사용 합니다.
  
1. Exchange 관리 센터에서 **준수 관리** 로 이동 \> **원본 위치 eDiscovery &amp; 유지**합니다.
    
2. 검색의 목록에서 2 단계에서에서 만든 검색을 선택 합니다.
    
3. **PST 파일로 내보내기를**클릭 합니다.
    
    ![PST 파일로 내보내기를 클릭합니다](media/4e59ae17-4541-43f4-a6d1-1f8b9ba9404b.png)
  
4. EDiscovery 내보내기 도구를 설치 하는 메시지가 표시 되 면 **실행**을 클릭 합니다.
    
5. EDiscovery PST 내보내기 도구에서에서 PST 파일을 다운로드 하려는 위치를 지정 하려면 **찾아보기** 를 클릭 합니다. 
    
    ![EDiscovery PST 내보내기 도구](media/17274d27-992e-4034-8133-8f793f554e6c.png)
  
    중복 제거를 사용 하도록 설정 하 고 검색할 수 없는 항목을 포함 하는 옵션을 무시할 수 있습니다.
    
6. 사용자의 컴퓨터에 PST 파일을 다운로드 하려면 **시작** 을 클릭 합니다. 
    
    내보내기 프로세스에 대 한 상태 정보를 표시 하는 **eDiscovery PST 내보내기 도구** 입니다. 내보내기가 완료 되 면 다운로드 한 위치에서 파일에 액세스할 수 있습니다. 
    
[Return to top](recover-deleted-items-in-a-mailbox.md#__top)
  
## <a name="step-5-restore-the-recovered-items-to-the-users-mailbox"></a>5 단계: 사용자의 사서함을 복구 된 항목 복원
<a name="step5"> </a>

마지막 단계는 사용자의 사서함을 복구 된 항목을 복원 하는 4 단계에서 내보낸 PST 파일을 사용 하는 것입니다. 사용자에 게 PST 파일을 보낸 후이 단계의 나머지 부분에서는 PST 파일을 열고 다음는 복구 된 항목을 자신의 사서함에 있는 다른 폴더로 이동 하는 사용자에 의해 수행 됩니다. 단계별 지침은 보낼 수도 있습니다 사용자 링크를이 항목에: [Open Outlook 데이터 파일 (.pst) 및](https://support.office.com/article/381b776d-7511-45a0-953a-0935c79d24f2)합니다. 또는 [삭제 된 항목을 PST 파일을 사용 하 여 사서함 복원](recover-deleted-items-in-a-mailbox.md#restoredeleteditems) 섹션에는 사용자 링크를 보낼 하 고 이러한 단계를 수행 하도록 요청 합니다. 
  
 **PST 파일을 사용자에 게 보내기**
  
마지막 단계를 수행 하는 사용자에 게 4 단계에서 내보낸 PST 파일을 보내는 됩니다. 몇 가지 방법으로이 작업을 수행 합니다.
  
- PST 파일을 전자 메일 메시지에 첨부 합니다. Outlook을 차단 PST 파일을 구성 하는 경우에 zip 파일 및 다음 메시지에 연결 해야 합니다. 다음은 방법:
    
1. Windows 탐색기나 파일 탐색기에서 PST 파일을 찾습니다.
    
2. 파일을 마우스 오른쪽 단추로 클릭 한 다음 **보내기** 를 선택 \> **압축 (zip) 폴더**입니다. Windows 새 zip 파일을 만들고 PST 파일로 동일한 이름을 제공 합니다.
    
3. 압축 된 PST 파일을 전자 메일 메시지에 첨부 하 고 파일 클릭 하 여 방금 후 압축을 수 있는 사용자에 게 보냅니다.
    
- PST 파일을 사용자에 액세스 하 고 검색할 수 있는 공유 폴더에 복사 합니다.
    
다음 섹션의 단계는 사용자가 사서함에 삭제 된 항목을 복원 하 여 수행 됩니다.
  
 **PST 파일을 사용 하 여 사서함을 삭제 된 항목 복원**
  
PST 파일을 사용 하 여 삭제 된 항목을 복원 하려면 Outlook 데스크톱 응용 프로그램을 사용 해야 합니다. Outlook Web App 또는 Outlook 웹에 있는 사용 하 여 PST 파일을 열 수는 없습니다.
  
1. Outlook 2013 또는 Outlook 2016에서 **파일** 탭을 클릭 합니다. 
    
2. 클릭 **Open &amp; 내보내기**, 다음 **Outlook 데이터 파일 열기**를 클릭 하 고 있습니다.
    
3. 전송 하는 관리자에 게 문의 하 여 PST 파일을 저장 한 위치로 이동 합니다.
    
4. PST를 선택한 다음 **열기**를 클릭 합니다.
    
    PST 파일로 Outlook의 왼쪽 탐색 모음에 표시 됩니다.
    
    ![PST 파일로 Outlook의 왼쪽 탐색 모음에 표시 됩니다.](media/c9389392-d08a-4aa7-848c-4986d448b0f2.png)
  
5. PST 파일을 확장 하 고 화살표를 클릭 하 고 복구 하려는 항목을 찾으려면 그 아래에 있는 폴더입니다.
    
    ![제거 폴더를 복구 하려는 항목에 대 한 있는지 확인](media/d4e372d9-ac23-4e95-8639-d8da690fefa7.png)
  
    > [!TIP]
    > 복구 하려는 항목에 대 한 제거 폴더를 찾습니다. 이것은 제거할 숨겨진된 폴더 항목으로 이동 됩니다. 이것이 가능성이 복구 하는 관리자에 게 문의이 폴더에 있는 항목입니다. 
  
6. 복구 하 고 **이동** 를 클릭 한 다음 원하는 항목을 마우스 오른쪽 단추로 클릭 \> **다른 폴더**입니다.
    
    ![이동을 클릭 하 고 다른 폴더를 선택 합니다](media/090063df-2aa0-444a-8e47-abd6fe6cf7a8.png)
  
7. 항목 이동 하 고 사용자의 받은 편지함에 **받은 편지함**클릭 한 다음 **확인**을 클릭 합니다.
    
    **팁:** 다른 종류의 항목을 복구 하려면 다음 중 하나를 수행 합니다. 
    
  - 일정 항목을 복구 하려면 마우스 오른쪽 단추로 클릭 하 고 **이동** 를 클릭 한 다음 \> **다른 폴더** \> **달력**입니다.
    
  - 대화 상대를 복구 하려면 마우스 오른쪽 단추로 클릭 하 고 **이동** 를 클릭 한 다음 \> **다른 폴더** \> **연락처**입니다.
    
  - 작업을 복구 하려면 마우스 오른쪽 단추로 클릭 하 고 **이동** 를 클릭 한 다음 \> **다른 폴더** \> **작업**합니다.
    
![다른 종류의 항목을 이동할 폴더를 선택 합니다.](media/f8290131-43f2-46f1-bc07-228c2d83b96c.png)
  
    Note that calendar items, contacts, and tasks are located directly in the Purges folder, and not in a Calendar, Contacts, or Tasks subfolder. However, you can sort by **Type** to group similar types of items. 
    
8. 완료 되 면 삭제 된 항목 복구, 왼쪽 탐색 모음에서 PST 파일을 마우스 오른쪽 단추로 클릭 하 고 **"이름 닫기 PST 파일의" "를**선택 합니다.
    
[Return to top](recover-deleted-items-in-a-mailbox.md#__top)
  
## <a name="more-information"></a>추가 정보
<a name="moreinfo"> </a>

- 항목에 대 한 삭제 된 항목 보존 기간 기간이 만료 되지 않도록 하는 경우 영구적으로 삭제 된 항목을 복구 하는 사용자에 대 한 수도 있습니다. 발생할 수 있는 관리자도 복구 가능한 항목 폴더에 지정 된 시간 항목은 복구에 사용할 수입니다. 예, 30 일에 대 한 사용자의 지운 편지함 폴더에 보관 된 모든 항목을 삭제 하는 정책 및 사용자가 다른 14 일 최대에 대 한 복구 가능한 항목 폴더에서 항목을 복구할 수 있는 다른 정책 있을 수 있습니다. 그러나 두 일 후 여전히 수 있습니다를이 항목의 절차를 사용 하 여 사용자의 사서함에 있는 항목을 복구 합니다.
    
- 사용자는 지워진 하지 않은 경우 및 해당 항목에 대 한 삭제 된 항목 보존 기간 기간이 만료 되지 않도록 하는 경우 삭제 된 항목을 복구할 수 있습니다. 사용자가 자신의 사서함에서 삭제 된 항목을 복구를 위해 다음 항목 중 하나를 가리킵니다.
    
  - [Windows용 Outlook에서 삭제된 항목 복구](https://support.office.com/article/49e81f3c-c8f4-4426-a0b9-c0fd751d48ce)
    
  - [Outlook 2010의 삭제 된 항목을 복구](https://support.office.com/article/cd9dfe12-8e8c-4a21-bbbf-4bd103a3f1fe)
    
  - [Outlook Web App에서 지운 편지함 또는 전자 메일 복구](https://support.office.com/article/c3d8fc15-eeef-4f1c-81df-e27964b7edd4)
    
  - [웹에 있는 Outlook에서 삭제 된 전자 메일 메시지를 복원 합니다.](https://support.office.com/article/a8ca78ac-4721-4066-95dd-571842e9fb11)
    
  - [Outlook에서 삭제 된 연락처를 복구 합니다.](https://support.office.com/article/51c83288-6888-4dcd-8c99-4932daabf643)
    
  - [Outlook.com에서 삭제 된 전자 메일 메시지를 복원 합니다.](https://go.microsoft.com/fwlink/p/?LinkID=623435)
    
[Return to top](recover-deleted-items-in-a-mailbox.md#__top)
  
