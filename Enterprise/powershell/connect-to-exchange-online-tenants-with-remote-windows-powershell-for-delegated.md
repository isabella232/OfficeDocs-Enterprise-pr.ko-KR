---
title: "DAP(위임된 액세스 권한) 파트너용 원격 Windows PowerShell을 사용하여 Exchange Online 테넌트에 연결"
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: 12/15/2017
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: 
ms.assetid: ae5f1a87-8b77-4f93-a1b8-56f800aeb283
description: "요약:DelegatedOrg 매개 변수를 사용하여 Exchange Online에 연결하도록 원격 Windows PowerShell을 사용합니다."
ms.openlocfilehash: 857c97e5d3374f293b98298419932af4ce2dfa19
ms.sourcegitcommit: 9f1fe023f7e2924477d6e9003fdc805e3cb6e2be
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/11/2018
---
# <a name="connect-to-exchange-online-tenants-with-remote-windows-powershell-for-delegated-access-permissions-dap-partners"></a>DAP(위임된 액세스 권한) 파트너용 원격 Windows PowerShell을 사용하여 Exchange Online 테넌트에 연결

 **요약:** _DelegatedOrg_ 매개 변수를 사용하여 Exchange Online에 연결하도록 원격 Windows PowerShell을 사용합니다.
  
원격 Windows PowerShell을 통해 명령줄에서 Exchange Online 설정을 관리할 수 있습니다. 로컬 컴퓨터에서 Windows PowerShell을 사용하여 원격 세션을 Exchange Online에 만듭니다. Exchange Online 자격 증명을 입력하고, 필수 연결 설정을 제공한 다음, 사용할 수 있도록 Exchange Online cmdlet을 로컬 Windows PowerShell 세션으로 가져오는 3단계 프로세스입니다.
  
## <a name="what-do-you-need-to-know-before-you-begin"></a>시작하기 전에 알아야 할 내용

- 예상 완료 시간: 5분
    
- 다음 Windows 버전을 사용할 수 있습니다.
    
  - Windows 10
    
  - Windows 8.1 또는 Windows 8
    
  - Windows Server 2012 R2 또는 Windows Server 2012
    
  - Windows 7 SP1(서비스 팩 1)*
    
  - Windows Server 2008 R2 SP1*
    
    * Microsoft .NET Framework 4.5.1 또는 .NET Framework 4.5를 설치한 다음 Windows Management Framework 4.0 또는 Windows Management Framework 3.0을 설치해야 합니다. 자세한 내용은 다음 리소스를 참조하세요.
    
  - [.NET Framework 설치](https://go.microsoft.com/fwlink/p/?LinkId=257868)
    
  - [Windows Management Framework 3.0](https://go.microsoft.com/fwlink/p/?LinkId=272757) 또는[Windows Management Framework 4.0](https://go.microsoft.com/fwlink/p/?LinkId=391344)
    
- 이 항목에서 절차에 적용할 수도 있는 키보드 바로 가기에 대한 자세한 내용은 [Exchange 관리 센터의 키보드 바로 가기](https://go.microsoft.com/fwlink/p/?LinkId=534017)를 참조하세요.
    
## 

> [!IMPORTANT]
> 이 절차는위임된 액세스 권한(DAP) 파트너전용입니다. DAP 파트너가 아닌 경우 이 절차를 사용해서는 안 됩니다. 
  
DAP 파트너는 신디케이션 및 CSP(클라우드 솔루션 공급자 파트너)입니다. 이러한 공급자는 다른 회사의 네트워크 또는 전자 통신 공급자인 경우가 많습니다. 구독을 고객에 대한 서비스 제공 사항으로 통합합니다. 또한 모든 고객 테넌트를 관리하고 보고할 수 있도록 Office 365고객 테넌트에 대해 AOBO(관리 위임자) 권한이 자동으로 부여되는 파트너 테넌트를 보유합니다.
  
## <a name="connect-to-exchange-online"></a>Exchange Online에 연결

1. 로컬 컴퓨터에서 Windows PowerShell을 열고 다음 명령을 실행합니다.
    
  ```
  $UserCredential = Get-Credential
  ```

    **Windows PowerShell 자격 증명 요청** 대화 상자에 DAP 관리자 사용자 이름과 암호를 입력한 다음 **확인**을 클릭합니다.
    
2. _<customer tenant domain name>_을 연결하려는 테넌트 도메인의 이름으로 교체하는 다음 명령을 실행합니다.
    
  ```
  $Session = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://ps.outlook.com/powershell-liveid?DelegatedOrg=<customer tenant domain name>-Credential $UserCredential -Authentication Basic -AllowRedirection
  ```

    이 명령에서 중요한 단계는 보고 정보에 액세스하는 고객을 지정하는 것입니다. 초기 도메인 이름의 FQDN을 값으로  _ConnectionURI_ 매개 변수에 제공하는 _DelegatedOrg_ 매개 변수에서 이를 수행합니다. 이는 연결할 끝점인 Exchange Online PowerShell 원격 Windows PowerShell에 대한 원격 Windows PowerShell을 의미합니다. 원격 Windows PowerShell은 보고서가 실행될 때마다 특정 고객의 컨텍스트에 보고되는 Office 365에 연결되어야 합니다. 이 고객이 지정되면 다음과 같은 모든 명령이 해당 고객의 컨텍스트에서 실행됩니다. 이를 통해 파트너는 이 고객에 대해 사용할 수 있는 모든 보고서에 액세스할 수 있습니다.
    
3. 다음 명령을 실행합니다.
    
  ```
  Import-PSSession $Session
  ```

> [!NOTE]
> 한 계정에 실행할 수 있는 동시 세션은 3개로 제한됩니다. 완료되면 원격 Windows PowerShell 세션의 연결을 끊어야 합니다. 세션 연결을 끊지 않고 Windows PowerShell 창을 닫으면 사용할 수 있는 원격 Windows PowerShell 세션을 전부 써버릴 수 있으며 세션이 만료될 때까지 기다려야 합니다. 원격 Windows PowerShell 세션의 연결을 끊으려면 다음 명령을 실행합니다. >  `Remove-PSSession $Session`
  
## <a name="how-do-you-know-this-worked"></a>작동 여부는 어떻게 확인합니까?

3단계를 수행하고 나면 Exchange Online cmdlet이 진행률 표시줄을 통해 추적한 대로 로컬 Windows PowerShell 세션으로 가져오기됩니다. 오류가 발생하지 않으면 정상적으로 연결된 것입니다. 빠르게 테스트하려면 Exchange Online cmdlet(예: **Get-Mailbox** )을 실행하여 결과를 확인합니다.
  
오류가 발생하면 다음 요구 사항을 확인합니다.
  
- 가장 흔한 문제는 암호를 잘못 입력한 경우입니다. 세 단계를 다시 실행하고 1단계에서 사용자 이름과 암호를 입력할 때 신중하게 확인하세요.
    
- DoS(서비스 거부) 공격을 방지하기 위해 Exchange Online 조직에 세 개의 개방형 원격 Windows PowerShell 연결만 사용해야 합니다.
    
- Windows PowerShell은 스크립트를 실행하도록 구성해야 합니다. 이 설정은 연결할 때마다 구성하는 것이 아니라 컴퓨터에서 한 번만 구성하면 됩니다. Windows PowerShell이 서명된 스크립트를 실행하도록 하려면 상승된 Windows PowerShell 창( **관리자 권한으로 실행**을 선택하여 열린 Windows PowerShell 창)에서 다음 명령을 실행합니다.
    
  ```
  Set-ExecutionPolicy RemoteSigned
  ```

- Exchange Online에 연결하는 데 사용하는 계정은 원격 Windows PowerShell에 대해 사용할 수 있어야 합니다. 자세한 내용은 [Exchange Online에서 원격 PowerShell 액세스 관리](https://go.microsoft.com/fwlink/p/?LinkId=534018)를 참조하세요.
    
- 로컬 컴퓨터와 Exchange Online 간에 TCP 포트 80 트래픽을 열어야 합니다. 이 포트는 이미 열려 있을 수도 있지만 조직에서 제한적인 인터넷 액세스 정책을 사용하는 경우에는 열려 있는지를 고려해야 합니다.
    
## <a name="call-the-cmdlet-directly-with-invoke-command"></a>Invoke-Command를 사용하여 cmdlet 직접 호출

원격 Windows PowerShell 세션을 가져오는 작업은 모든 Exchange Online cmdlet에서 가져오므로 시간이 오래 걸리는 프로세스일 수 있습니다. 이는 일괄 처리에 문제가 될 수 있습니다(예: 다른 테넌트에 대한 보고서를 실행하거나 대량 변경 시). **Import-PSSession** 사용에 대한 대안으로 **Invoke-Command** 로 사용하려는 cmdlet을 직접 호출할 수 있습니다. 예: **get-mailbox** cmdlet를 호출하려면 `Import-PSSession $Session`에 대해 이 구문을 대체합니다.
  
```
Invoke-Command -Session $Session -ScriptBlock {Get-Mailbox}
```

## <a name="more-reporting-cmdlets"></a>자세한 보고 cmdlet 내용

이 항목에서 사용한 cmdlet은 Windows PowerShell cmdlet입니다. 이러한 cmdlet에 대한 자세한 내용은 다음 항목을 참조하세요.
  
- [Get-Credential](https://go.microsoft.com/fwlink/p/?LinkId=389618)
    
- [New-PSSession](https://go.microsoft.com/fwlink/p/?LinkId=389621)
    
- [Import-PSSession](https://go.microsoft.com/fwlink/p/?LinkId=389619)
    
- [Remove-PSSession](https://go.microsoft.com/fwlink/p/?LinkId=389620)
    
- [Set-ExecutionPolicy](https://go.microsoft.com/fwlink/p/?LinkId=389623)
    
