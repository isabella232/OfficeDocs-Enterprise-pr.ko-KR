---
title: Office 365 PowerShell을 사용하여 SharePoint Online 사용자 및 그룹 관리
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 05/01/2018
ms.audience: Admin
ms.topic: hub-page
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- PowerShell
- Ent_Office_Other
ms.assetid: d0d3877a-831f-4744-96b0-d8167f06cca2
description: '요약: SharePoint Online 사용자, 그룹 및 사이트를 관리 하려면 Office 365 PowerShell를 사용 합니다.'
ms.openlocfilehash: 8ed40d2c736853145e21f0f9852bdb18c7842075
ms.sourcegitcommit: 74cdb2534bce376abc9cf4fef85ff039c46ee790
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/03/2018
---
# <a name="manage-sharepoint-online-users-and-groups-with-office-365-powershell"></a>Office 365 PowerShell을 사용하여 SharePoint Online 사용자 및 그룹 관리

 **요약:** Office 365 PowerShell을 사용 하 여 SharePoint Online 사용자, 그룹 및 사이트를 관리할 수 있습니다.

SharePoint Online 작동 하는 사용자 계정 또는 그룹의 큰 목록 및가 보다 쉽게 관리할 수 있는 경우에 Office 365 PowerShell을 사용할 수 있습니다. 

## <a name="before-you-begin"></a>시작하기 전에

이 항목의 절차에서는 SharePoint Online에 연결 해야 합니다. 자세한 내용은 [Connect to SharePoint Online PowerShell를](https://docs.microsoft.com/en-us/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps) 참조 하십시오.

## <a name="get-a-list-of-sites-groups-and-users"></a>사이트, 그룹, 사용자 목록 가져오기

사용자 및 그룹 관리를 시작하려면 먼저 사이트, 그룹 및 사용자 목록을 가져와야 합니다. 그리고 나면 해당 정보를 이 문서의 예제 전반에 걸쳐 사용할 수 있습니다.

### <a name="get-a-list-of-sites"></a>사이트 목록 가져오기

이 명령을 사용하여 테넌트의 사이트 목록을 가져옵니다.

```
Get-SPOSite
```

### <a name="get-a-list-of-groups"></a>그룹 목록 가져오기

이 명령을 사용하여 테넌트의 그룹 목록을 가져옵니다.

```
Get-SPOSite | ForEach-Object {Get-SPOSiteGroup -Site $_.Url} |Format-Table
```

### <a name="get-a-list-of-users"></a>사용자 목록 가져오기

이 명령을 사용하여 테넌트의 사용자 목록을 가져옵니다.

```Get-SPOSite | ForEach-Object {Get-SPOUser -Site $_.Url}```

## <a name="add-a-user-to-the-site-collection-administrators-group"></a>사이트 모음 관리자 그룹에 사용자 추가

**Set-spouser** 명령을 사용 하 여 사이트 모음에서 사이트 모음 관리자의 목록에 사용자를 추가 합니다. 다음은 구문을 표시 하는 방법입니다.

```
$tenant = "tenant"
<!--This is the Tenant Name. Value must be enclosed in double quotation marks. Example: "Contoso01"-->
$site = "site"
<!--# This is the Site name. Value must be enclosed in double quotation marks. Example: "contosotest"-->
$user = "loginname"
<!--This is the users login name. Value must be enclosed in double quotation marks. Example "opalc"-->
Set-SPOUser -Site https://$tenant.sharepoint.com/sites/$site -LoginName $user@$tenant.onmicrosoft.com -IsSiteCollectionAdmin $true
 ```

이 예제에서는 변수를 사용 하 여 값을 저장 하 고 스크립트에서 메모에 (예 "<!--This is the Tenant Name…-->") 해야 해당 값을 파악할 수 있습니다.

예,이 명령 집합에 추가 하는 Opal Castillo (사용자 이름 opalc) 사이트 모음 관리자의 목록 contoso1 테 넌 트의 ContosoTest 사이트 모음:

```
$tenant = "contoso1"
$site = "contosotest"
$user = "opalc"
Set-SPOUser -Site https://$tenant.sharepoint.com/sites/$site -LoginName $user@$tenant.onmicrosoft.com -IsSiteCollectionAdmin $true
```

실제로 이러한 명령을 잘라내 메모장에 붙여넣고 사용 중인 환경에서 $tenant, $site, $user 변수 값을 변경한 다음 SharePoint Online 관리 셸 창에 붙여넣을 수 있습니다.

## <a name="add-a-user-to-other-site-collection-administrators-groups"></a>다른 사이트 모음 관리자 그룹에 사용자 추가

이 작업에서는 하겠습니다 사용 하 여 **Add-spouser** 명령을 사이트 모음에서 SharePoint 그룹에 사용자를 추가 합니다. 다음은 구문을 표시 하는 방법입니다.

```
$tenant = "tenant"
<!--This is the Tenant Name. Value must be enclosed in double quotation marks. Example: "Contoso01"-->
$site = "site"
<!--This is the Site name. Value must be enclosed in double quotation marks. Example: "contosotest"-->
$user = "loginname"
<!--This is the users login name. Value must be enclosed in double quotation marks. Example: "opalc"-->
$group = "group"
<!--This is the SharePoint security Group name. Value must be enclosed in double quotation marks. Example: "Auditors"-->
Add-SPOUser -Group $group -LoginName $user@$tenant.onmicrosoft.com -Site https://$tenant.sharepoint.com/sites/$site

```

예, 보겠습니다 협곡 투성이 (사용자 이름 glenr) 그룹에 추가 감사자 contoso1 테 넌 트의 ContosoTest 사이트 모음에서:

```
$tenant = "contoso1"
$site = "contosotest"
$user = "glenr"
$group = "Auditors"
Add-SPOUser -Group $group -LoginName $user@$tenant.onmicrosoft.com -Site https://$tenant.sharepoint.com/sites/$site
```

## <a name="create-a-site-collection-group"></a>사이트 모음 그룹 만들기

**Set-spositegroup** 명령을 사용 하 여 새 SharePoint 그룹 만들기 및 ContosoTest 사이트 모음에 추가 합니다. 다음은 구문을 표시 하는 방법입니다.

```
$tenant = "tenant"
<!--This is the Tenant Name. Value must be enclosed in double quotation marks, Example: "Contoso01"-->
$site = "site"
<!--This is the Site name. Value must be enclosed in double quotation marks, Example: "contosotest"-->
$group = "group"
<!--This is the SharePoint security Group name. Value must be enclosed in double quotation marks, Example: "Auditors"-->
$level = "permission level"
<!--This is the level of permissions to assign to the group. Value must be enclosed in double quotation marks, Example: "View Only"-->
New-SPOSiteGroup -Group $group -PermissionLevels $level -Site https://$tenant.sharepoint.com/sites/$site
```

> [!IMPORTANT]
> 따옴표로 공백이 포함 된 모든 문자열을 묶어야 합니다. **Set-spositegroup** cmdlet을 사용 하 여 사용 권한 수준 등의 그룹 속성을 나중에 업데이트할 수 있습니다.

예, contoso1 테 넌 시에서 Contoso 테스트 사이트 모음에 추가 보기 전용 권한이 있는 감사자 그룹 보겠습니다.

```
$tenant = "contoso1"
$site = "Contoso Test"
$level = "View Only"
$group = "Auditors"
New-SPOSiteGroup -Group $group -PermissionLevels $level -Site https://$tenant.sharepoint.com/sites/$site
```

## <a name="remove-users-from-a-group"></a>그룹에서 사용자 제거

사이트 하나 또는 모든 사이트에서 사용자를 제거해야 하는 경우가 있습니다. 직원이 사업부를 이동하거나 퇴사하는 경우를 예로 들 수 있습니다. 직원이 한 명이라면 UI에서 이 작업을 쉽게 수행할 수 있습니다. 그러나 전체 사업부를 사이트 간에 이동해야 하는 경우에는 쉽지 않습니다.

그러나 SharePoint Online 관리 셸 및 CSV 파일을 사용 하 여이 빠르고 쉽게 합니다. 이 작업에서 사이트 모음 보안 그룹에서 사용자를 제거 하려면 Windows PowerShell을 사용 합니다. 그런 다음 CSV 파일을 사용 하 고 다른 사이트에서 많은 사용자를 제거 합니다. 

**Remove-spouser** 명령을 명령 구문을 볼 수 있도록 사이트 모음 그룹에서 단일 Office 365 사용자를 제거 하려면 사용할 것 것입니다. 구문을 표시 되는 모양을 다음과 같습니다.

```
$tenant = "tenant"
<!--This is the Tenant Name. Value must be enclosed in double quotation marks, Example: "Contoso01"-->
$site = "site"
<!--This is the Site name. Value must be enclosed in double quotation marks, Example: "contosotest"-->
$group = "group"
<!--This is the SharePoint security Group name. Value must be enclosed in double quotation marks, Example: "Auditors"-->
$user = "loginname"
<!--This is the user’s login name. Value must be enclosed in double quotation marks, Example: "opalc"-->
Remove-SPOUser -LoginName $user@$tenant.onmicrosoft.com -Site https://$tenant.sharepoint.com/sites/$site
```

예, contoso1 테 넌 시에서 Contoso 테스트 사이트 모음에서 사이트 모음 감사자 그룹에서 제거 Bobby Overby 보겠습니다 합니다.

```
$tenant = "contoso1"
$site = "contosotest"
$user = "bobbyo"
$group = "Auditors"
Remove-SPOUser -LoginName $user@$tenant.onmicrosoft.com -Site https://$tenant.sharepoint.com/sites/$site -Group $group
```

다음으로는 Bobby를 현재 포함되어 있는 모든 그룹에서 제거해 보겠습니다.

```
$tenant = "contoso1"
$user = "bobbyo"
Get-SPOSite | ForEach-Object {Get-SPOSiteGroup –Site $_.Url} | ForEach-Object {Remove-SPOUser -LoginName $user@$tenant.onmicrosoft.com -Site &_.Url}
```

> [!WARNING]
> 이 스크립트는 작업 방법을 설명하기 위한 용도로만 제공됩니다. 실제로 사용자가 퇴사하는 경우 등 모든 그룹에서 사용자를 제거해야 하는 경우가 아니면 이 명령을 실행해서는 안 됩니다.

## <a name="automate-management-of-large-lists-of-users-and-groups"></a>대형 사용자 및 그룹 목록의 관리 자동화

SharePoint 사이트에 많은 수의 계정 추가 및 사용 권한을 부여할 Office 365 관리 센터, 개별 PowerShell 명령 또는 PowerShell를 사용할 수 있는 CSV 파일입니다. 이러한 선택 항목 중 CSV 파일이이 작업을 자동화 하는 가장 빠른 방법입니다.

기본 프로세스에 해당 하는 Windows PowerShell 스크립트 필요한 매개 변수는 헤더 (열)를 가진 CSV 파일을 만드는 것입니다. Excel에서 이러한 목록의 쉽게 만들 수 있으며 다음 CSV 파일로 내보낼 수 있습니다. Windows PowerShell 스크립트를 사용 하 여 그룹 및 사이트에 그룹에 사용자 추가 (영문) CSV 파일의 레코드 (행)를 통해 반복 하는 다음 합니다. 

예를 들어 사이트 모음, 그룹 및 사용 권한 그룹을 정의하는 CSV 파일을 만들어 보겠습니다. 다음으로는 CSV 파일을 만들어 그룹에 사용자를 채웁니다. 마지막으로 그룹을 만들고 채우는 간단한 Windows PowerShell 스크립트를 만들어 실행합니다.

다음과 같은 구조의 첫 번째 CSV 파일은 하나 이상의 그룹을 하나 이상의 사이트 모음에 추가합니다.

### <a name="header"></a>머리글:

```
Site,Group,PermissionLevels
```

### <a name="item"></a>항목:

```
https://tenant.sharepoint.com/sites/site,site collection,group,level
```

예제 파일은 다음과 같습니다.

```
Site,Group,PermissionLevels
https://contoso1.sharepoint.com/sites/contosotest,Contoso Project Leads,Full Control
https://contoso1.sharepoint.com/sites/contosotest,Contoso Auditors,View Only
https://contoso1.sharepoint.com/sites/contosotest,Contoso Designers,Design
https://contoso1.sharepoint.com/sites/TeamSite01,XT1000 Team Leads,Full Control
https://contoso1.sharepoint.com/sites/TeamSite01,XT1000 Advisors,Edit
https://contoso1.sharepoint.com/sites/Blog01,Contoso Blog Designers,Design
https://contoso1.sharepoint.com/sites/Blog01,Contoso Blog Editors,Edit
https://contoso1.sharepoint.com/sites/Project01,Project Alpha Approvers,Full Control
```

다음과 같은 구조의 두 번째 CSV 파일은 한 명 이상의 사용자를 하나 이상의 그룹에 추가합니다.

### <a name="header"></a>머리글:

```
Group,LoginName,Site
```

### <a name="item"></a>항목:

```
group,login,https://tenant.sharepoint.com/sites/site
```

예제 파일은 다음과 같습니다.

```
Group,LoginName,Site
Contoso Project Leads,bobbyo@contoso1.onmicrosoft.com,https://contoso1.sharepoint.com/sites/contosotest
Contoso Auditors,allieb@contoso1.onmicrosoft.com,https://contoso1.sharepoint.com/sites/contosotest
Contoso Designers,bonniek@contoso1.onmicrosoft.com,https://contoso1.sharepoint.com/sites/contosotest
XT1000 Team Leads,dorenap@contoso1.onmicrosoft.com,https://contoso1.sharepoint.com/sites/TeamSite01
XT1000 Advisors,garthf@contoso1.onmicrosoft.com,https://contoso1.sharepoint.com/sites/TeamSite01
Contoso Blog Designers,janets@contoso1.onmicrosoft.com,https://contoso1.sharepoint.com/sites/Blog01
Contoso Blog Editors,opalc@contoso1.onmicrosoft.com,https://contoso1.sharepoint.com/sites/Blog01
Project Alpha Approvers,robinc@contoso1.onmicrosoft.com,https://contoso1.sharepoint.com/sites/Project01
```

그런 다음 해당 드라이브에 CSV 파일 두 개가 저장되어 있어야 합니다. 다음 명령은 두 CSV 파일을 모두 사용하여 권한 및 그룹 멤버십을 추가합니다.

```
Import-Csv C:\O365Admin\GroupsAndPermissions.csv | ForEach-Object {New-SPOSiteGroup -Group $_.Group -PermissionLevels $_.PermissionLevels -Site $_.Site}
Import-Csv C:\O365Admin\Users.csv | ForEach-Object {Add-SPOUser -Group $_.Group –LoginName $_.LoginName -Site $_.Site}
```

스크립트는 CSV 파일 내용을 가져오고 (굵게)에서 열에 값을 사용 하 여 **새로 SPOSiteGroup** 및 **Add-spouser** 명령의 매개 변수를 채웁니다. 이 예제에서는 C 드라이브에 저장 되는 있지만 원하는 위치에 관계 없이 저장할 수 있습니다.

다음으로 동일한 CSV 파일을 사용해 서로 다른 사이트의 여러 그룹에서 사용자 여러 명을 제거해 보겠습니다. 명령은 다음과 같습니다.

```
Import-Csv C:\O365Admin\Users.csv | ForEach-Object {Remove-SPOUser -LoginName $_.LoginName -Site $_.Site -Group $_.Group}
```

## <a name="generate-user-reports"></a>사용자 보고서 생성

사이트 몇 개에 대해 간단한 보고서를 가져와 해당 사이트의 사용자, 사용자의 사용 권한 수준 및 기타 속성을 표시할 수 있습니다. 이 작업을 위한 구문은 다음과 같습니다.

```
$tenant = "tenant"
<!--This is the Tenant Name. Value must be enclosed in double quotes, Example: "Contoso01"-->
$site = "site"
<!--This is the Site name. Value must be enclosed in double quotes, Example: "contosotest"-->
Get-SPOUser -Site https://$tenant.sharepoint.com/sites/$site | select * | Format-table -Wrap -AutoSize | Out-File c\UsersReport.txt -Force -Width 360 -Append
```

이러한 세 사이트에 대 한 데이터를 가져오려면 그러면 되 고 해당 사용자의 로컬 드라이브에 텍스트 파일에 쓰기. 이때 매개 변수는-Append 기존 파일에 새 콘텐츠를 추가 합니다.

예를 들어 Contoso1 테넌트의 ContosoTest, TeamSite01 및 Project01 사이트에 대한 보고서를 실행해 보겠습니다.

```
$tenant = "contoso1"
$site = "contosotest"
Get-SPOUser -Site https://$tenant.sharepoint.com/sites/$site | Format-Table -Wrap -AutoSize | Out-File c:\UsersReport.txt -Force -Width 360 -Append
$site = "TeamSite01"
Get-SPOUser -Site https://$tenant.sharepoint.com/sites/$site |Format-Table -Wrap -AutoSize | Out-File c:\UsersReport.txt -Force -Width 360 -Append
$site = "Project01"
Get-SPOUser -Site https://$tenant.sharepoint.com/sites/$site | Format-Table -Wrap -AutoSize | Out-File c:\UsersReport.txt -Force -Width 360 -Append
```

참고만 **$site** 변수를 변경 해야 합니다. 명령의 세 연속 영역이 모두을 통해 해당 값을 유지 하는 **$tenant** 변수입니다.

모든 사이트에 대해 이 작업을 수행하려는 경우 다음 명령을 사용하면 모든 웹 사이트를 입력하지 않고도 작업을 수행할 수 있습니다.

```
Get-SPOSite | ForEach-Object {Get-SPOUser –Site $_.Url} | Format-Table -Wrap -AutoSize | Out-File c:\UsersReport.txt -Force -Width 360 -Append
```

이 보고서는 매우 간단 하 고 더 많은 보다 구체적인 보고서 또는 보다 자세한 정보를 포함 하는 보고서를 만드는 코드를 추가할 수 있습니다. 하지만이 방법을 사용 해야 SharePoint 온라인 환경에서 사용자를 관리 하려면 SharePoint Online 관리 셸을 사용 하는 방법의 얻을 수 있습니다.
   
## <a name="see-also"></a>참고 항목

[SharePoint Online PowerShell에 연결](https://docs.microsoft.com/en-us/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps)

[Office 365 PowerShell을 사용하여 SharePoint Online 관리](create-sharepoint-sites-and-add-users-with-powershell.md)

[Office 365 PowerShell 사용한 Office 365 관리](manage-office-365-with-office-365-powershell.md)
  
[Office 365 PowerShell 시작](getting-started-with-office-365-powershell.md)
