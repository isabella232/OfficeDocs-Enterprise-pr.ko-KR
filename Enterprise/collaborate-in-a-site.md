---
title: 사이트에서 게스트와 공동 작업
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
audience: ITPro
ms.topic: article
ms.service: sharepoint-online
localization_priority: Normal
description: SharePoint 사이트에서 게스트와 공동 작업 하는 방법에 대해 알아봅니다.
ms.openlocfilehash: 4b68b50fec4322f12c24969bdd71e7d9c0fda245
ms.sourcegitcommit: d388c76d25ca67f240db97f7bfc90f0991b0e7f8
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/17/2019
ms.locfileid: "37017316"
---
# <a name="collaborate-with-guests-in-a-site"></a><span data-ttu-id="c495e-103">사이트에서 게스트와 공동 작업</span><span class="sxs-lookup"><span data-stu-id="c495e-103">Collaborate with guests in a site</span></span>

<span data-ttu-id="c495e-104">여러 문서, 데이터 및 목록에서 게스트와 공동 작업을 수행 해야 하는 경우에는 SharePoint 사이트를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c495e-104">If you need to collaborate with guests across documents, data, and lists, you can use a SharePoint site.</span></span> <span data-ttu-id="c495e-105">최신 SharePoint 사이트는 사이트 구성원 자격을 관리 하 고 공유 사서함 및 일정과 같은 추가 공동 작업 도구를 제공할 수 있는 Office 365 그룹에 연결 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c495e-105">Modern SharePoint sites are connected to Office 365 Groups which can manage the site membership and provide additional collaboration tools such as a shared mailbox and calendar.</span></span>

<span data-ttu-id="c495e-106">이 문서에서는 게스트가 포함 된 공동 작업을 위해 SharePoint 사이트를 설정 하는 데 필요한 Microsoft 365 구성 단계를 안내 합니다.</span><span class="sxs-lookup"><span data-stu-id="c495e-106">In this article, we'll walk through the Microsoft 365 configuration steps necessary to set up a SharePoint site for collaboration with guests.</span></span>

## <a name="azure-organizational-relationships-settings"></a><span data-ttu-id="c495e-107">Azure 조직 관계 설정</span><span class="sxs-lookup"><span data-stu-id="c495e-107">Azure Organizational relationships settings</span></span>

<span data-ttu-id="c495e-108">Microsoft 365의 공유는 Azure Active Directory의 조직 관계 설정에 따라 최상위 수준에서 관리 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c495e-108">Sharing in Microsoft 365 is governed at its highest level by the organizational relationships settings in Azure Active Directory.</span></span> <span data-ttu-id="c495e-109">Azure AD에서 게스트 공유가 사용 하지 않도록 설정 되거나 제한 되 면 Microsoft 365에서 구성한 모든 공유 설정이 재정의 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c495e-109">If guest sharing is disabled or restricted in Azure AD, this will override any sharing settings that you configure in Microsoft 365.</span></span>

<span data-ttu-id="c495e-110">조직 관계 설정을 확인 하 여 게스트가 공유 하는 것이 차단 되지 않는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="c495e-110">Check the organizational relationships settings to ensure that sharing with guests is not blocked.</span></span>

![Azure Active Directory 조직 관계 설정 페이지 스크린샷](media/azure-ad-organizational-relationships-settings.png)

<span data-ttu-id="c495e-112">조직 관계 설정을 설정 하려면</span><span class="sxs-lookup"><span data-stu-id="c495e-112">To set organizational relationship settings</span></span>

1. <span data-ttu-id="c495e-113">Microsoft Azure에 로그인 [https://portal.azure.com](https://portal.azure.com)합니다.</span><span class="sxs-lookup"><span data-stu-id="c495e-113">Log in to Microsoft Azure at [https://portal.azure.com](https://portal.azure.com).</span></span>
2. <span data-ttu-id="c495e-114">왼쪽 탐색 창에서 **Azure Active Directory**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="c495e-114">In the left navigation, click **Azure Active Directory**.</span></span>
3. <span data-ttu-id="c495e-115">**개요** 창에서 **조직 관계**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="c495e-115">In the **Overview** pane, click **Organizational relationships**.</span></span>
4. <span data-ttu-id="c495e-116">**조직 관계** 창에서 **설정을**클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="c495e-116">In the **Organizational relationships** pane, click **Settings**.</span></span>
5. <span data-ttu-id="c495e-117">**Guest inviter 역할의 관리자 및 사용자가 초대** 를 하 고 **구성원은 초대** 를 할 수 있는지 확인 하 고 둘 다 **예**로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="c495e-117">Ensure that **Admins and users in the guest inviter role can invite** and **Members can invite** are both set to **Yes**.</span></span>
6. <span data-ttu-id="c495e-118">변경한 경우 **저장**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="c495e-118">If you made changes, click **Save**.</span></span>

<span data-ttu-id="c495e-119">**공동 작업 제한** 섹션의 설정을 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="c495e-119">Note the settings in the **Collaboration restrictions** section.</span></span> <span data-ttu-id="c495e-120">공동 작업 하려는 게스트의 도메인이 차단 되지 않았는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="c495e-120">Make sure that the domains of the guests that you want to collaborate with aren't blocked.</span></span>

## <a name="office-365-groups-guest-settings"></a><span data-ttu-id="c495e-121">Office 365 그룹 게스트 설정</span><span class="sxs-lookup"><span data-stu-id="c495e-121">Office 365 Groups guest settings</span></span>

<span data-ttu-id="c495e-122">최신 SharePoint 사이트에서는 Office 365 그룹을 사용 하 여 사이트 액세스를 제어 합니다.</span><span class="sxs-lookup"><span data-stu-id="c495e-122">Modern SharePoint sites use Office 365 Groups to control site access.</span></span> <span data-ttu-id="c495e-123">SharePoint 사이트에서 게스트 액세스를 작동 하려면 Office 365 그룹 게스트 설정이 설정 되어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c495e-123">The Office 365 Groups guest settings must be turned on in order for guest access in SharePoint sites to work.</span></span>

![Microsoft 365 관리 센터의 Office 365 그룹 게스트 설정 스크린샷](media/office-365-groups-guest-settings.png)

<span data-ttu-id="c495e-125">Office 365 그룹 게스트 설정을 설정 하려면</span><span class="sxs-lookup"><span data-stu-id="c495e-125">To set Office 365 Groups guest settings</span></span>

1. <span data-ttu-id="c495e-126">Microsoft 365 관리 센터의 왼쪽 탐색 영역에서 **설정을**확장 합니다.</span><span class="sxs-lookup"><span data-stu-id="c495e-126">In the Microsoft 365 admin center, in the left navigation, expand **Settings**.</span></span>
2. <span data-ttu-id="c495e-127">**서비스 & 추가 기능**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="c495e-127">Click **Services & add-ins**.</span></span>
3. <span data-ttu-id="c495e-128">목록에서 **Office 365 그룹**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="c495e-128">In the list, click **Office 365 Groups**.</span></span>
4. <span data-ttu-id="c495e-129">**조직 외부 구성원이 그룹 콘텐츠에 액세스** 하 고 그룹 **소유자가 조직 외부의 사람을 그룹에 추가** 하도록 허용 확인란을 모두 선택 했는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="c495e-129">Ensure that the **Let group members outside your organization access group content** and **Let group owners add people outside your organization to groups** check boxes are both checked.</span></span>
5. <span data-ttu-id="c495e-130">변경한 경우 **변경 내용 저장**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="c495e-130">If you made changes, click **Save changes**.</span></span>


## <a name="sharepoint-organization-level-sharing-settings"></a><span data-ttu-id="c495e-131">SharePoint 조직 수준 공유 설정</span><span class="sxs-lookup"><span data-stu-id="c495e-131">SharePoint organization level sharing settings</span></span>

<span data-ttu-id="c495e-132">게스트가 SharePoint 사이트에 액세스할 수 있도록 하려면 SharePoint 조직 수준 공유 설정에서 guests 공유를 허용 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c495e-132">In order for guests to have access to SharePoint sites, the SharePoint organization-level sharing settings must allow for sharing with guests.</span></span>

<span data-ttu-id="c495e-133">조직 수준 설정에 따라 개별 사이트에 사용할 수 있는 설정이 결정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c495e-133">The organization-level settings determine what settings are available for individual sites.</span></span> <span data-ttu-id="c495e-134">사이트 설정은 조직 수준 설정 보다는 더 이상 허용 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c495e-134">Site settings cannot be more permissive than the organization-level settings.</span></span>

<span data-ttu-id="c495e-135">익명 사용자와 파일 및 폴더 공유를 허용 하려면 **모든 사용자**를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="c495e-135">If you want to allow file and folder sharing with anonymous users, choose **Anyone**.</span></span> <span data-ttu-id="c495e-136">모든 게스트가 인증을 받도록 하려면 **신규 및 기존 게스트**를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="c495e-136">If you want to ensure that all guests have to authenticate, choose **New and existing guests**.</span></span> <span data-ttu-id="c495e-137">조직의 모든 사이트에 필요한 가장 관대 한 설정을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="c495e-137">Choose the most permissive setting that will be needed by any site in your organization.</span></span>

![SharePoint 조직 수준 공유 설정 스크린샷](media/sharepoint-organization-external-sharing-controls.png)


<span data-ttu-id="c495e-139">SharePoint 조직 수준 공유 설정을 설정 하려면</span><span class="sxs-lookup"><span data-stu-id="c495e-139">To set SharePoint organization level sharing settings</span></span>

1. <span data-ttu-id="c495e-140">Microsoft 365 관리 센터의 왼쪽 탐색에 있는 **관리 센터**에서 **SharePoint**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="c495e-140">In the Microsoft 365 admin center, in the left navigation, under **Admin centers**, click **SharePoint**.</span></span>
2. <span data-ttu-id="c495e-141">SharePoint 관리 센터의 왼쪽 탐색 창에서 **공유**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="c495e-141">In the SharePoint admin center, in the left navigation, click **Sharing**.</span></span>
3. <span data-ttu-id="c495e-142">SharePoint 용 외부 공유가 **사용자** 또는 **신규 및 기존 게스트로**설정 되어 있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="c495e-142">Ensure that external sharing for SharePoint is set to **Anyone** or **New and existing guests**.</span></span>
4. <span data-ttu-id="c495e-143">변경한 경우 **저장**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="c495e-143">If you made changes, click **Save**.</span></span>

## <a name="create-a-site"></a><span data-ttu-id="c495e-144">사이트 만들기</span><span class="sxs-lookup"><span data-stu-id="c495e-144">Create a site</span></span>

<span data-ttu-id="c495e-145">다음 단계는 게스트와 공동 작업 하는 데 사용할 사이트를 만드는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="c495e-145">The next step is to create the site that you plan to use for collaborating with guests.</span></span>

<span data-ttu-id="c495e-146">사이트를 만들려면</span><span class="sxs-lookup"><span data-stu-id="c495e-146">To create a site</span></span>
1. <span data-ttu-id="c495e-147">SharePoint 관리 센터의 **사이트**아래에서 **활성 사이트**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="c495e-147">In the SharePoint admin center, under **Sites**, click **Active sites**.</span></span>
2. <span data-ttu-id="c495e-148">
            \**만들기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c495e-148">Click **Create**.</span></span>
3. <span data-ttu-id="c495e-149">**팀 사이트**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="c495e-149">Click **Team site**.</span></span>
4. <span data-ttu-id="c495e-150">사이트 이름을 입력 하 고 그룹 소유자 (사이트 소유자)의 이름을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="c495e-150">Type a site name and enter a name for the Group owner (site owner).</span></span>
5. <span data-ttu-id="c495e-151">**고급 설정**에서이 사이트를 공용 또는 개인 사이트로 설정할 것인지 여부를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="c495e-151">Under **Advanced settings**, choose if you want this to be a public or private site.</span></span>
6. <span data-ttu-id="c495e-152">**다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c495e-152">Click **Next**.</span></span>
7. <span data-ttu-id="c495e-153">**마침**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c495e-153">Click **Finish**.</span></span>

<span data-ttu-id="c495e-154">나중에 사용자를 초대 합니다.</span><span class="sxs-lookup"><span data-stu-id="c495e-154">We'll invite users later.</span></span> <span data-ttu-id="c495e-155">다음으로이 사이트에 대 한 사이트 수준 공유 설정을 확인 하는 것이 중요 합니다.</span><span class="sxs-lookup"><span data-stu-id="c495e-155">Next, it's important to check the site-level sharing settings for this site.</span></span>

## <a name="sharepoint-site-level-sharing-settings"></a><span data-ttu-id="c495e-156">SharePoint 사이트 수준 공유 설정</span><span class="sxs-lookup"><span data-stu-id="c495e-156">SharePoint site level sharing settings</span></span>

<span data-ttu-id="c495e-157">사이트 수준 공유 설정을 확인 하 여 해당 사이트에 대해 원하는 액세스 유형을 허용 하는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="c495e-157">Check the site-level sharing settings to make sure that they allow the type of access that you want for this site.</span></span> <span data-ttu-id="c495e-158">예를 들어 조직 수준 설정을 모든 **사용자**로 설정 했지만 모든 게스트가이 사이트에 대해 인증을 받으려는 경우에는 사이트 수준 공유 설정이 **신규 및 기존 게스트로**설정 되어 있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="c495e-158">For example, if you set the organization-level settings to **Anyone**, but you want all guests to authenticate for this site, then make sure the site-level sharing settings are set to **New and existing guests**.</span></span>

<span data-ttu-id="c495e-159">사이트는 익명 사용자 (**모든 사용자** 설정)와 공유할 수 없지만 개별 파일 및 폴더는 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c495e-159">Note that the site cannot be shared with anonymous users (**Anyone** setting), but individual files and folders can.</span></span>

![SharePoint 사이트 외부 공유 설정 스크린샷](media/sharepoint-site-external-sharing-settings.png)

<span data-ttu-id="c495e-161">사이트 수준 공유 설정을 설정 하려면</span><span class="sxs-lookup"><span data-stu-id="c495e-161">To set site-level sharing settings</span></span>
1. <span data-ttu-id="c495e-162">SharePoint 관리 센터의 왼쪽 탐색 창에서 **사이트** 를 확장 하 고 **활성 사이트**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="c495e-162">In the SharePoint admin center, in the left navigation, expand **Sites** and click **Active sites**.</span></span>
2. <span data-ttu-id="c495e-163">방금 만든 사이트를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="c495e-163">Select the site that you just created.</span></span>
3. <span data-ttu-id="c495e-164">리본 메뉴에서 **공유**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="c495e-164">In the ribbon, click **Sharing**.</span></span>
4. <span data-ttu-id="c495e-165">공유가 **사용자** 또는 **신규 및 기존 게스트로**설정 되어 있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="c495e-165">Ensure that sharing is set to **Anyone** or **New and existing guests**.</span></span>
5. <span data-ttu-id="c495e-166">변경한 경우 **저장**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="c495e-166">If you made changes, click **Save**.</span></span>

## <a name="invite-users"></a><span data-ttu-id="c495e-167">사용자 초대</span><span class="sxs-lookup"><span data-stu-id="c495e-167">Invite users</span></span>

<span data-ttu-id="c495e-168">게스트 공유 설정이 이제 구성 되므로 사이트에 내부 사용자 및 게스트를 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c495e-168">Guest sharing settings are now configured, so you can start adding internal users and guests to your site.</span></span> <span data-ttu-id="c495e-169">사이트 액세스는 연결 된 Office 365 그룹을 통해 제어 되므로 사용자를 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c495e-169">Site access is controlled through the associated Office 365 Group, so we'll be adding users there.</span></span>

<span data-ttu-id="c495e-170">그룹에 내부 사용자를 초대 하려면</span><span class="sxs-lookup"><span data-stu-id="c495e-170">To invite internal users to a group</span></span>
1. <span data-ttu-id="c495e-171">사용자를 추가 하려는 사이트로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="c495e-171">Navigate to the site where you want to add users.</span></span>
2. <span data-ttu-id="c495e-172">오른쪽 위에 있는 **구성원** 을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="c495e-172">Click **Members** in the upper right.</span></span>
3. <span data-ttu-id="c495e-173">**구성원 추가**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c495e-173">Click **Add members**.</span></span>
4. <span data-ttu-id="c495e-174">사이트에 초대할 사용자의 이름 또는 전자 메일 주소를 입력 하 고 **저장**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="c495e-174">Type the names or email addresses of the users that you want to invite to the site, and then click **Save**.</span></span>

<span data-ttu-id="c495e-175">게스트 사용자는 사이트에서 추가할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="c495e-175">Guest users can't be added from the site.</span></span> <span data-ttu-id="c495e-176">웹에서 Outlook을 사용 하 여 추가 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c495e-176">You need to add them using Outlook on the web.</span></span>

<span data-ttu-id="c495e-177">사이트에 게스트를 초대 하려면</span><span class="sxs-lookup"><span data-stu-id="c495e-177">To invite guests to a site</span></span>
1. <span data-ttu-id="c495e-178">웹용 Outlook의 **그룹**에서 구성원을 추가 하려는 그룹을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="c495e-178">In Outlook on the web, under **Groups**, click the group where you want to add members.</span></span>
2. <span data-ttu-id="c495e-179">그룹 대화 상대 카드를 열고 **기타 옵션** (...)에서 **구성원 추가**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="c495e-179">Open the group contact card, and then, under **More options** (...), click **Add members**.</span></span>
3. <span data-ttu-id="c495e-180">초대 하려는 게스트의 전자 메일 주소를 입력 한 다음 **추가**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="c495e-180">Type the email addresses of the guests that you want to invite, and then click **Add**.</span></span>
4. <span data-ttu-id="c495e-181">**닫기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c495e-181">Click **Close**.</span></span>

## <a name="see-also"></a><span data-ttu-id="c495e-182">참고 항목</span><span class="sxs-lookup"><span data-stu-id="c495e-182">See Also</span></span>